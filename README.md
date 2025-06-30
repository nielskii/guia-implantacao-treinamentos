# Guia de Implantação - Módulo Web Fictício: Plataforma de Treinamentos Internos

## 1. Visão Geral
O módulo "Plataforma de Treinamentos Internos" permite que usuários acessem, acompanhem, assistem e realizam tarefas vinculadas a projetos. Será integrado ao sistema corporativo de gestão já existente e acessado por meio da intranet da empresa.

## 2. Pré-requisitos
- Node.js 18+
- PHP 8.2+
- MySQL 8.0+
- NPM 9+
- Git 2.30+
- Editor de código
- Insomnia 10+
- Navegador
- Laravel 10.0
- Vue.js 3.0
- Docker 24+
- Redis 7.0
- Acesso SSH ao servidor de desenvolvimento e homologação
- Permissão de escrita em diretórios de logs e storage.
- Acesso a base de dados com permissão de leitura, escrita e estrutura
- Credenciais de API de serviços externos
- Permissão de push/pull no repositório Git

## 3. Especificações Técnicas
- **Arquitetura:** Arquitetura baseada em microsserviços, com um frontend em Vue.js que consome APIs REST desenvolvidas em Laravel.O backend se comunica com o banco de dados MySQL e utiliza Redis para filas de tarefas assincronas. O sistema é hospedado em containers Docker orquestrados por Docker Compose no ambiente de desenvolvimento.
- **Tecnologias:**
  - Linguagens: PHP, JavaScript
  - Banco de dados: MySQL
  - Bibliotecas e frameworks: Laravel 10, Vue.js 3, Axios, Redis e Bootstrap 5
- **Configurações:**
  - Variáveis de ambiente: `.env`
    - `APP_NAME`, `APP_ENV`, `APP_DEBUG`, `APP_URL`
    - `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`
    - ``MAIL_MAILER`, `MAIL_HOST`, `MAIL_PORT`, `MAIL_USERNAME`, `MAIL_PASSWORD`
    - `QUEUE_CONNECTION=redis`, `CACHE_DRIVER=redis`
  - Parâmetros de conexão definidos no banco de dados definidos em `.env` e `config/database.php`. 
 - Serviços de e-mail é o `SMTP` configurado via `.env`.   
 - Cache e filas: Redis definido em `config/cache.php` e `confing/queue.php`.

## 4. Procedimento Padrão de Registro de Implantação
1. Data/hora: 10/06/2023 às 15:00
2. Responsável: Daniel Souza - Analista de Sistemas
3. Servidor alvo: `intranet-app01.empresa.com.br`
4. Versão do artefato: v1.0.0
5. Comentários: Implantação concluída com sucesso. Todos os testes automatizados e manuais passaram. Backup validado antes do deploy. Primeiros acessos confirmados por usuários-chave.

## 5. Checklist de Implantação
- [x] Planejamento concluído
- [x] Ambiente preparado
- [x] Deploy executado
- [x] Testes de validação realizados
- [x] Logs revisados

## 6. Validação e Testes
- Testes de carga simulando 300 acessos simultâneos. O sistema manteve estabilidade e tempo médio de resposta abaixo de 800ms durante os testes, sem quedas de serviço.
- Testes funcionais: Login e autenticação e usuários, listagem e acesso aos treinamentos, reprodução de video-aulas, submissão de tarefas e acompanhamento de progresso e geração de certificado ao final do curso.
- Testes de integração: envio de e-mail ao conclusão de curso via serviço SMTP, registro de progresso no banco de dados e integração com o sistema interno de RH para atualização do status dos colaboradores.
## 7. Avaliação e Feedback
- Problema encontrado: atraso no envio de e-mails em produção
- Solução: ajuste no serviço de fila (configurado Redis em produção)
- Sugestão: Adicionar testes automatizados específicos para uploads de arquivos, realizar testes de integração com o serviço de e-mail já no ambiente de homologação, configurar monitoramento com alertas automáticos para APIs críticas e criar um checklist interno de verificação de permissões e roles de usuários antes do deploy.

## 8. Anexos
- [Documentação Técnica]
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/docs/introducao-tecnica.md)
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/docs/manual-usuario.md)

- [Script de Migração de Banco]
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/scripts/init-db.sql)
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/scripts/seeds.sql)
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/scripts/.env.example)

- [Modelo de Relatório de Testes]
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/testes/relatorio-validacao.md)
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/testes/checklist.md)
  - (https://github.com/nielskii/guia-implantacao-treinamentos/blob/main/testes/incidentes.md)
