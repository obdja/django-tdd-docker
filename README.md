# django-tdd-docker
django-tdd-docker

run docker wsl2

sudo -b unshare --pid --fork --mount-proc /lib/systemd/systemd --system-unit=basic.target

docker 

docker-compose build

docker-compose up -d

docker-compose down -v

docker-compose up -d --build

docker-compose exec movies pytest




# normal run
$ docker-compose exec movies pytest

# disable warnings
$ docker-compose exec movies pytest -p no:warnings

# run only the last failed tests
$ docker-compose exec movies pytest --lf

# run only the tests with names that match the string expression
$ docker-compose exec movies pytest -k "movie and not all_movies"

# stop the test session after the first failure
$ docker-compose exec movies pytest -x

# enter PDB after first failure then end the test session
$ docker-compose exec movies pytest -x --pdb

# stop the test run after two failures
$ docker-compose exec movies pytest --maxfail=2

# show local variables in tracebacks
$ docker-compose exec movies pytest -l

# list the 2 slowest tests
$ docker-compose exec movies pytest --durations=2

****


>>> heroku --version

>heroku create

Creating app... done, ⬢ secret-headland-28614
https://secret-headland-28614.herokuapp.com/ | https://git.heroku.com/secret-headland-28614.git

>heroku container:login
[](https://secret-headland-28614.herokuapp.com/admin/login/?next%3D%2Fadmin%2F)
>docker build -f Dockerfile.prod -t registry.heroku.com/secret-headland-28614/web .

>heroku config:get DATABASE_URL --app secret-headland-28614

postgres://fepurpavnhaziv:b33b83db4759370d9548035a624ea588c9bd4dee460a7357e5c02dbce149b9e5@ec2-3-211-221-185.compute-1.amazonaws.com:5432/d2r16j71bjmdar

> export DATABASE_URL=postgres://fepurpavnhaziv:b33b83db4759370d9548035a624ea588c9bd4dee460a7357e5c02dbce149b9e5@ec2-3-211-221-185.compute-1.amazonaws.com:5432/d2r16j71bjmdar

> docker push registry.heroku.com/secret-headland-28614/web:latest

>heroku container:release web --app secret-headland-28614

>heroku run python manage.py migrate --app secret-headland-28614
>heroku run python manage.py loaddata movies.json --app secret-headland-28614

coverage

docker-compose exec movies pytest -p no:warnings --cov=.
docker-compose exec movies pytest -p no:warnings --cov=. --cov-report html

docker-compose exec movies flake8 .
docker-compose exec movies black --check --exclude=migrations .
docker-compose exec movies isort . --check-only
docker-compose exec movies isort . --diff
docker-compose exec movies isort .

