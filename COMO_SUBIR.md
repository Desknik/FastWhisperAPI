# Documentação - Subindo o Stack Docker "ai kit"

Este projeto utiliza Docker Compose para orquestrar três serviços principais:
- FastWhisperAPI (transcrição de áudio)
- n8n (automação de workflows, com ffmpeg)
- Kokoro (API FastAPI)

## Pré-requisitos
- Docker instalado ([Download Docker](https://www.docker.com/get-started/))
- Docker Compose instalado (normalmente já incluso no Docker Desktop)

## Passos para subir o stack

1. **Clone ou acesse o diretório do projeto:**
   ```bash
   cd "g:/projects/AI KIT/FastWhisperAPI"
   ```

2. **(Opcional) Edite variáveis de ambiente:**
   - Por padrão, o FastWhisperAPI detecta CPU/GPU automaticamente.
   - Se quiser forçar uso de CPU, adicione `FORCE_CPU=true` nas variáveis de ambiente do serviço no `docker-compose.yml`.

3. **Suba os containers:**
   ```bash
   docker-compose up -d
   ```
   Isso irá:
   - Construir a imagem do FastWhisperAPI
   - Baixar as imagens do n8n e kokoro
   - Iniciar todos os serviços em segundo plano

4. **Acesse os serviços:**
   - FastWhisperAPI: http://localhost:8000
   - n8n: http://localhost:5678
   - Kokoro: http://localhost:8880

5. **Parar os containers:**
   ```bash
   docker-compose down
   ```

## Observações
- O serviço n8n já vem com ffmpeg instalado via entrypoint customizado.
- O stack está em uma rede Docker chamada `ai_kit`.
- Para persistência de dados do n8n, descomente o volume no serviço n8n no `docker-compose.yml`.

---
Dúvidas ou problemas? Consulte a documentação de cada serviço ou abra uma issue.
