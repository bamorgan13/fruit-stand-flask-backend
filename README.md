# Deploying Flask Backend directly (no Docker)

# Create a Procfile with the command to run when the app starts (I'm upgrading my db and then running flask on the port that heroku creates) 
echo "web: flask db upgrade && flask run --host=0.0.0.0 -p $PORT" > Procfile

# Create a heroku app
heroku create -a fruitnodocker

# Push to heroku
git add .
git commit -m"Prep heroku deployment"
git push heroku master

# Provision database on heroku
provision database (on heroku website: resources -> search postgres -> heroku postgres -> provision)

# Seed my database by piping a sql file into postgres (you may not need this since you have your seeds in your revisions)
cat ./heroku_seeds.sql | heroku pg:psql -a fruitnodocker