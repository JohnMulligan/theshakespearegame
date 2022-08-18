# deployment documentation

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-flask.html
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-rds.html#python-rds-create
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/RelatedResources.html?icmpid=docs_elasticbeanstalk_console
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.Procedural.Importing.NonRDSRepl.html


https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.Procedural.Importing.SmallExisting.html


incredible: https://stackoverflow.com/questions/62479386/no-module-named-application-error-while-deploying-simple-web-app-to-elastic-be

https://www.alcortech.com/steps-to-deploy-python-flask-mysql-application-on-aws-elastic-beanstalk/

New workflow. The above all consistently failed. Could not connect to the database?

CREATED A FREE-TIER RDBS, trying this: https://guimauve.io/articles/deploy-flask-app-on-aws-part-1-db-and-eb-env



Having a sql dump/reimport issue, due to engine versions I think.
mysql -u root -p shakespeare < shakespeare.sql is throwing an error.
solving with
sed -i 's/utf8mb4_0900_ai_ci/utf8mb4_unicode_ci/g' shakespeare.sql


mysql.server start
	eb init
	eb create ariel

later, to redeploy:
	eb deploy