.DEFAULT_GOAL := up
.PHONY: up build down restart stop ssh tinker logs status test

up:
	@echo "Bringing up services."
	docker-compose up -d

build:
	@echo "Building services."
	docker-compose build

down:
	@echo "Shutting down services."
	docker-compose down

stop:
	@echo "Stopping services."
	docker-compose stop

restart:
	@echo "Restarting services."
	docker-compose restart

logs:
	@echo "Watching logs.."
	docker-compose logs --tail 100 -f

stats:
	docker stats

status:
	docker-compose ps

export-queue-definitions:
	curl -u rabbitmq:secret -X GET http://127.0.0.160:15672/api/definitions > .docker/rabbitmq/definitions.json