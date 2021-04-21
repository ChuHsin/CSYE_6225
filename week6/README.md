

Every time you make changes on the config file, you will need to restart the agent,

You replace the CloudWatch Agent config file, every time when you deploy the application.

When you start your application server not EC2, you run these command to re-configure your CloudWatch to pick up the latest configuration you have.

Insight is expensive.

Go to Metrics


        logger.log({
            level: 'info',
            message: ''
        });
                client.increment('');