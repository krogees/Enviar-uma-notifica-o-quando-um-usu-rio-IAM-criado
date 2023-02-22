Na Amazon Web Services (AWS), você pode usar esse padrão para implantar um modelo do AWS CloudFormation para receber notificações automaticamente quando os usuários do AWS Identity and Access Management (IAM) são criados. 

Usando o IAM, você pode gerenciar o acesso aos serviços e recursos da AWS com segurança. Você pode criar e gerenciar usuários e grupos da AWS e usar permissões para permitir e negar a esses usuários e grupos o acesso aos recursos da AWS.

O modelo do CloudFormation cria um evento do Amazon CloudWatch Events e uma função do AWS Lambda. O evento usa o AWS CloudTrail para monitorar qualquer usuário do IAM que está sendo criado na conta da AWS. Se um usuário for criado, o evento CloudWatch Events iniciará uma função do Lambda, que enviará uma notificação do Amazon Simple Notification Service (Amazon SNS) informando sobre o novo evento de criação do usuário.

# Pré-requisitos e limitações
Pré-requisitos
Uma conta ativa da AWS

AWS CloudTrail criada e implantada

Limitações 
O modelo do AWS CloudFormation deve ser implantado somente para CreateUser. 

Create the S3 bucket for the Lambda script:

- Open the Amazon S3 console, and choose or create an S3 bucket. This S3 bucket will host the Lambda code .zip file. The S3 bucket name cannot contain leading slashes.

Upload the Lambda code to the S3 bucket:

- Upload the Lambda code .zip file provided in the Attachments section to the S3 bucket that you defined.

Deploy the CloudFormation template:

- On the CloudFormation console, deploy the CloudFormation New_Create_IAM_User.yml template that's provided as an attachment to this pattern. In the next epic, provide values for the template parameters.

Complete the parameters in the CloudFormation template:

- Enter the name of the S3 bucket that you created or chose in the first epic.

Provide the S3 key:
- Provide the location of the Lambda code .zip file in your S3 bucket, without leading slashes (for example, <directory>/<file-name>.zip).

Provide an email address:
- Provide an active email address to receive Amazon SNS notifications.

Define the logging level:
- Define the logging level and frequency for your Lambda function. Info designates detailed informational messages on the application’s progress. Error designates error events that could still allow the application to continue running. Warning designates potentially harmful situations.

Confirm the subscription:
- When the template successfully deploys, it sends a subscription email message to the email address provided. To receive notifications, you must confirm this email subscription.
