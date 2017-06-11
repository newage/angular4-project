config: ## создание конфига для докера
		cp -u .env.dev .env
install: ## Сборка имиджа
		docker-compose build
console: ## Подключение к контейнеру
		docker-compose run --rm -p 4200:4300 angular bash