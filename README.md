# Tutorial de Build com GitHub Actions

Este tutorial mostra como usar a CLI do GitHub (gh) para gerenciar o build do projeto.

## Pré-requisitos

1. Instale a CLI do GitHub:
```bash
sudo apt-get install gh
```

2. Faça login no GitHub:
```bash
gh auth login
```

## Comandos Básicos

### Verificar Status do Repositório
```bash
git status
```

### Verificar Workflows Disponíveis
```bash
gh workflow list
```

### Acionar Build Manualmente
```bash
gh workflow run "Docker Build and Push"
```

### Verificar Status do Build
```bash
gh run list --workflow=docker-build-push.yml
```

### Verificar Logs do Build
```bash
gh run view --log --job=<ID_DO_JOB>
```

## Dicas Importantes

1. O workflow usa o runner padrão do GitHub (`ubuntu-latest`)
2. Não são necessárias dependências externas (apenas biblioteca padrão do Python)
3. A imagem Docker é construída e publicada no GitHub Container Registry

## Problemas Comuns e Soluções

1. **Erro de Permissão no Registry**
   - Verifique as permissões do workflow no arquivo `.github/workflows/docker-build-push.yml`
   - Certifique-se que as permissões estão configuradas corretamente:
   ```yaml
   permissions:
     contents: read
     packages: write
     id-token: write
   ```

2. **Erro no Build do Docker**
   - Verifique o Dockerfile
   - Consulte os logs do build usando `gh run view --log`

## Links Úteis

- Documentação oficial do GitHub CLI: https://cli.github.com/manual/
- GitHub Actions: https://docs.github.com/en/actions
