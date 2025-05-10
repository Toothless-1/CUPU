# Приложение Кредитного Скоринга — это приложение для банков для расчета кредитоспособности клиентов и принятия решений о выдаче кредитов.
Для того, чтобы была возможность запустить приложение, на устройстве должен быть установлен Docker и Docker Compose.\
Запуск сервиса осуществляется через docker-compose файл.\
Все необходимые версии библиотек прописаны в requierments.txt файле. \
Пример requierments.txt \
fastapi==0.110.0 \
uvicorn==0.27.0 \
cloudpickle>=2.1.1 #вместо джоблиба \
lightgbm==4.2.0 \
typing>=1.0 \
woe-iv-bin==0.1.2 \
scikit-learn==1.2.2 \
numpy==1.26.4 \
pandas==2.2.2 \
matplotlib==3.8.3 \
Команды для запуска проекта: \
Очистка предыдущих сборок \
docker system prune -a --volumes \
docker-compose down -v --remove-orphans \
Сборка с учетом изменений \
docker-compose build --no-cache \
docker-compose up -d 
