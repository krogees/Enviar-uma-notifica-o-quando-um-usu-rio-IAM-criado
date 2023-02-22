# Na Amazon Web Services (AWS), você pode usar esse padrão para implantar um modelo do AWS CloudFormation para receber notificações automaticamente quando os usuários do AWS Identity and Access Management (IAM) são criados. 

Usando o IAM, você pode gerenciar o acesso aos serviços e recursos da AWS com segurança. Você pode criar e gerenciar usuários e grupos da AWS e usar permissões para permitir e negar a esses usuários e grupos o acesso aos recursos da AWS.

O modelo do CloudFormation cria um evento do Amazon CloudWatch Events e uma função do AWS Lambda. O evento usa o AWS CloudTrail para monitorar qualquer usuário do IAM que está sendo criado na conta da AWS. Se um usuário for criado, o evento CloudWatch Events iniciará uma função do Lambda, que enviará uma notificação do Amazon Simple Notification Service (Amazon SNS) informando sobre o novo evento de criação do usuário.

# Pré-requisitos e limitações
Pré-requisitos
Uma conta ativa da AWS

Uma trilha do AWS CloudTrail criada e implantada

Limitações 
O modelo do AWS CloudFormation deve ser implantado somente para CreateUser. 
