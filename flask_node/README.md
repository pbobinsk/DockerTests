1.
docker compose up --build -d

docker compose down

2.
docker swarm init

docker build -t flask_app:latest ../../PythonTests/docker_python_web_app
docker build -t node_api:latest ../../JavaScriptTests/docker_node_api_service 

docker stack deploy -c .\swarm-compose.yml moja_apka

docker stack ls
docker service ls

docker stack rm moja_apka      

3.
docker build -t flask_app:v2 ../../PythonTests/docker_python_web_app

update_config w swarm.yml
docker service update --image flask_app:v2 moja_apka_flask_app
docker service update --rollback moja_apka_flask_app
docker service ps moja_apka_flask_app

4.
docker build -t flask_app:v3 ../../PythonTests/docker_python_web_app

update_config w swarm.yml
docker service update --image flask_app:v3 moja_apka_flask_app
docker service ps moja_apka_flask_app






