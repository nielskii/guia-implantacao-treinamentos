# Incidentes e Soluções

**Erro:** Envio de e-mails atrasado  
**Causa:** SMTP em modo síncrono  
**Solução:** Habilitado uso de Redis para filas assíncronas

**Erro:** Bug no upload de arquivos PDF  
**Causa:** Falha na validação de extensão  
**Solução:** Ajustado validador no backend
