Na Amazon Web Services (AWS), você pode usar esse padrão para implantar um modelo do AWS CloudFormation para receber notificações automaticamente quando os usuários do AWS Identity and Access Management (IAM) são criados. 

Usando o IAM, você pode gerenciar o acesso aos serviços e recursos da AWS com segurança. Você pode criar e gerenciar usuários e grupos da AWS e usar permissões para permitir e negar a esses usuários e grupos o acesso aos recursos da AWS.

O modelo do CloudFormation cria um evento do Amazon CloudWatch Events e uma função do AWS Lambda. O evento usa o AWS CloudTrail para monitorar qualquer usuário do IAM que está sendo criado na conta da AWS. Se um usuário for criado, o evento CloudWatch Events iniciará uma função do Lambda, que enviará uma notificação do Amazon Simple Notification Service (Amazon SNS) informando sobre o novo evento de criação do usuário.

# Pré-requisitos e limitações
Pré-requisitos
Uma conta ativa da AWS

AWS CloudTrail criada e implantada

Limitações 
O modelo do AWS CloudFormation deve ser implantado somente para CreateUser. 

Criar o bucket S3 para o script Lambda:

    Abra o console do Amazon S3 e escolha ou crie um bucket S3. Esse bucket S3 hospedará o arquivo zip do código Lambda . . O nome do bucket S3 não pode conter barras iniciais.

Faça o upload do código Lambda para o bucket S3:

    Faça o upload do arquivo zip do código . do Lambda fornecido na seção Anexos para o bucket S3 que você definiu.

Implantar o modelo do CloudFormation:

    No console do CloudFormation, implante o modelo CloudFormation New_Creapfte IAM_User.yml que é fornecido como um anexo a este padrão. No próximo épico, forneça valores para os parâmetros do modelo.

Complete os parâmetros no modelo do CloudFormation:

    Digite o nome do bucket S3 que você criou ou escolheu no primeiro épico.

Fornecer a chave S3:

    Forneça o local do arquivo. zip do código Lambda no bucket S3, sem barras de início (por exemplo, /.zip).

Forneça um endereço de e-mail:

    Forneça um endereço de e-mail ativo para receber notificações do Amazon SNS.

Definir o nível de registo:

    Defina o nível de registro e a frequência para sua função do Lambda. Info designa mensagens informativas detalhadas sobre o progresso da aplicação. Erro designa eventos de erro que ainda podem permitir que o aplicativo continue funcionando. Aviso designa situações potencialmente prejudiciais.

Confirmar a subscrição:

    Quando o modelo é implantado com sucesso, ele envia uma mensagem de e-mail de assinatura para o endereço de e-mail fornecido. Para receber notificações, você deve confirmar esta assinatura de e-mail.
