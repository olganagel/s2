# I. Практика
1. **Запуск docker-compose**:
   ```bash
   docker-compose up -d

2. **Подключение к mongos**:

   ```bash
   docker exec -it mongos_router mongosh

3. **Инициализация конфигурационного сервера**:

   ```bash
   rs.initiate({
      _id: "config_server",
      members: [{_id: 0, host: "configSrv:27017"}],
          configsvr: true,
      version: 1
    });

4. **Инициализация шардов с репликами**:

   ```bash
   rs.initiate(
    {
        _id: "shard1", 
        members: [
            {_id: 0, host: "shard1:27018"},
            {_id: 1, host: "shard1:27028"},
            {_id: 2, host: "shard1:27038"}], 
            version: 1});

   rs.initiate(
    {
        _id: "shard2", 
        members: [
            {_id: 0, host: "shard2:27019"},
            {_id: 1, host: "shard2:27029"},
            {_id: 2, host: "shard2:27039"}], 
            version: 1});

5. **Добавление шардов в кластер**:

   ```bash
   sh.addShard("shard1/shard1:27018");
   sh.addShard("shard2/shard2:27019");

6. **Включение шардирования БД**:

   ```bash
   sh.enableSharding("somedb");
   sh.shardCollection("somedb.helloDoc", {"_id": "hashed"});

7. **Проверка статуса шардирования**:

   ```bash
   sh.status();

8. **Включение кеширования**:

   ```bash
   REDIS_URL: "redis://redis_1:6379"; 

9. **Проверка кеширования**:
   
   ```bash
   curl http://localhost:8080/helloDoc/users

# II. Схема
https://drive.google.com/file/d/1ELOKZpuVxH4WKBUKmHo3X6D05SSijMmd/view?usp=sharing
