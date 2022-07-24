# Microsserviços

## Fluxo
Front > API Gateway > Microsserviços > Banco de dados (específico pra cada um ou unificado)

## Comuniação entre serviços
Síncrona => HTTP Rest
Assíncrona => AMQP Messageria (Rabbit MQ, Kafka, etc)

## API Gateway
Não deixamos os serviços expostos para o front.

O API Gateway serve de middleware para comunicar entre o front e serviços, buscando pela porta e IP do serviço requisitado.

Aqui cadastramos todos os serviços e para onde estaremos direcionando.

Ex: Frontend => :80 => API Gateway => /users => 8001, /products => 8002, /purchase => 8003, /checkout => 8004

Temos uma segurança maior pois o cliente não irá saber quais são os serviços e as portas de acesso.

Temos API Gateway da Amazon, do GCP, Azure e Kong.

Autenticação é configurada aqui também.

## Características
- Escalabilidade: podemos aumentar/diminuir recursos para serviços específicos ao invés de ser para toda uma aplicação monolítica, gerando economia.

- Multiplas linguagens.

- Atentar a DDD.

## Configurações importantes:
- **Monitoramento**: para saber se algum serviço caiu ou os picos de uso.

- **Curcuit Breaker**: quando um serviço precisa se comunicar com outro, mas está fora, precisa ter uma tratativa, ex:

    - Colocar o serviço dentro de uma fila para ficar chamando até obter a informação que deseja.
    - Ter um banco de dados em cache para conseguir a informação.

## Quando começar a usar microsserviços
- Precisa entender do negócio da empresa.
- Tamanho da equipe: qnto maior o time, mais conflitos podem ocorrer no merge em aplicações monolíticas.
- Maturidade do negócio: já consegue ter um gerencimento melhor, tem equipe de infra, etc.. 