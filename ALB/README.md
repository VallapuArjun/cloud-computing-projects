
# Create an Application Load Balancer (ALB):
## Log in to AWS Console:
* Log in to your AWS account console.

## Navigate to Elastic Load Balancing:
* Go to the "Services" menu, and select "Elastic Load Balancing."

## Create Load Balancer:
* Click on "Create Load Balancer."

## Choose Load Balancer Type:
* Select "Application Load Balancer."

## Configure Load Balancer:

* Give your load balancer a name.
* Choose the appropriate VPC.
* Configure the availability zones where your instances are located.
## Configure Security Settings (Optional):
You can configure an SSL/TLS certificate for HTTPS if needed.

## Configure Security Groups:
Choose security groups that allow incoming traffic to your ALB.

## Configure Routing:

* Create a new target group or use an existing one.
* Choose the protocol and port for the target group.
* Choose the health check settings.
## Register Targets:
* Choose the instances you want to register with the target group.These are the instances that will receive incoming traffic.

## Review and Create:
* Review your settings and click "Create" to create the ALB.

## Formulate Target Groups and Associate Instances:
## Create a Target Group:
* After creating the ALB, navigate to "Target Groups" in the left sidebar, and click on "Create target group."

## Configure Target Group:

* Give your target group a name.
* Choose the protocol and port.
* Choose the target type (instance or IP).
* Set health check settings.
## Register Targets:
* Register the EC2 instances that you want to balance traffic among. You can choose instances from your VPC and attach them to the target group.

## Associate Target Group with ALB:
* Go back to your ALB configuration, and under the "Listeners" section, edit the listener rules. Add a new rule that forwards incoming traffic to your target group.

## Test Load Balancing:
* Once configured, your ALB will distribute incoming traffic to the registered instances based on the rules you've set. You can test this by accessing the ALB's DNS name in a web browser.

