.PHONY: build
build:
	@docker-compose build

.PHONY: up
up:
	@docker-compose up tor-proxy

.PHONY: upd
upd:
	@docker-compose up -d tor-proxy

.PHONY: run-u
run-u:
	@docker-compose run --rm wp-scan --proxy socks5h://tor-proxy:9050 --url ${url} --enumerate u

.PHONY: run-p
run-p:
	@docker-compose run -it --rm wp-scan --proxy socks5h://tor-proxy:9050 --url ${url} -U ${username} --passwords /passwordlists/passwords.lst

.PHONY: down
down:
	@docker-compose down
