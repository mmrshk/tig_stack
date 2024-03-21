### Compose project for Telegraf, InfluxDB, Grafana, Nginx, Rails app with MongoDB and ElasticSearch 

This an example project to show the TIG (Telegraf, InfluxDB and Grafana) stack and hot it monitors rails app.

<img width="1905" alt="Screenshot 2024-03-21 at 16 51 38" src="https://github.com/mmrshk/tig_stack/assets/31416671/02bbb698-c0a1-484c-852a-96ccd6c52a2e">

## Start the stack with docker compose

```bash
$ docker-compose up
```

## Services and Ports

### Grafana
- URL: http://localhost:3001
- User: admin 
- Password: admin 

### Telegraf
- Port: 8125 UDP (StatsD input)

### InfluxDB
- Port: 8086 (HTTP API)
- User: admin 
- Password: admin 
- Database: influx

### Rails app
- URL: http://localhost:3000

### Nginx
- URL: http://localhost:80

## Give permissions for docker
```
docker-compose exec telegraf sh
cd var/run
ls -la
chmod 777 docker.sock
```

## Look after metrics
To test on a load use such commands:

```bash
docker-compose exec rails_test rake 'populate_post:creation[50]'
docker-compose exec rails_test rake 'populate_post:persistence'
docker-compose exec rails_test rake 'populate_post:deletion'
docker-compose exec rails_test rake 'populate_post:match_all_search'
```

### Results
## System
<img width="1887" alt="Screenshot 2024-03-21 at 16 52 17" src="https://github.com/mmrshk/tig_stack/assets/31416671/38736be0-8394-4f15-9066-a4db4e63d3fe">
<img width="1994" alt="Screenshot 2024-03-21 at 16 52 38" src="https://github.com/mmrshk/tig_stack/assets/31416671/cbf0b6fb-6e7a-4664-84cd-6dc04d732e25">

## Nginx
<img width="2001" alt="Screenshot 2024-03-21 at 16 53 00" src="https://github.com/mmrshk/tig_stack/assets/31416671/82e096ff-c619-4c79-9124-fb2ecf4425e4">

## ElasticSearch
<img width="1995" alt="Screenshot 2024-03-21 at 16 54 13" src="https://github.com/mmrshk/tig_stack/assets/31416671/cc49d871-0118-4f45-b550-d56bd1aaa5dd">
<img width="2008" alt="Screenshot 2024-03-21 at 16 53 32" src="https://github.com/mmrshk/tig_stack/assets/31416671/e375401b-629e-478b-9af6-9387a2c7f2df">
<img width="1991" alt="Screenshot 2024-03-21 at 16 53 21" src="https://github.com/mmrshk/tig_stack/assets/31416671/d46c0e90-de35-47d2-acbc-4d0663f7a17d">

## Mongo
<img width="1991" alt="Screenshot 2024-03-21 at 16 55 25" src="https://github.com/mmrshk/tig_stack/assets/31416671/7a6d6c71-973a-44cc-9c75-836362432d48">
<img width="1998" alt="Screenshot 2024-03-21 at 16 55 05" src="https://github.com/mmrshk/tig_stack/assets/31416671/5d124d18-745f-4f81-93ed-a1dbe7395819">
<img width="2003" alt="Screenshot 2024-03-21 at 16 54 32" src="https://github.com/mmrshk/tig_stack/assets/31416671/b6b46c7d-cafc-47ab-8a95-23428f2ea627">

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.

