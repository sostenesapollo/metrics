# 🚀 Configuração para Coolify

## Problema Comum: Erro de Montagem de Arquivos

Se você está recebendo um erro como:
```
error mounting ".../prometheus.yml" to rootfs at "/etc/prometheus/prometheus.yml": 
cannot create subdirectories: not a directory
```

## Solução

### 1. Garantir que todos os arquivos estão no Git

Certifique-se de que todos os arquivos de configuração estão commitados:

```bash
git add prometheus.yml otel-collector-config.yaml docker-compose.yml
git add grafana/provisioning grafana/dashboards
git commit -m "feat: Adiciona configurações de monitoramento"
git push
```

### 2. No Coolify

1. **Verifique o Diretório Base**: No Coolify, certifique-se de que o diretório base do projeto está configurado corretamente
2. **Force um novo deploy**: Após fazer push, force um novo deploy no Coolify
3. **Verifique os logs**: Os logs devem mostrar se os arquivos estão sendo encontrados

### 3. Arquivos Necessários

Os seguintes arquivos devem estar no repositório:
- ✅ `docker-compose.yml`
- ✅ `prometheus.yml`
- ✅ `otel-collector-config.yaml`
- ✅ `grafana/provisioning/dashboards/dashboard.yml`
- ✅ `grafana/provisioning/datasources/prometheus.yml`
- ✅ `grafana/dashboards/pedegas-metrics.json`

### 4. Se o problema persistir

Se mesmo após commitar os arquivos o erro continuar, pode ser um problema de contexto no Coolify. Nesse caso:

1. Verifique se o diretório de trabalho do Coolify está correto
2. Considere usar paths absolutos (mas isso geralmente não é necessário)
3. Verifique as permissões dos arquivos no servidor

## Estrutura de Arquivos

```
metrics/
├── docker-compose.yml
├── prometheus.yml
├── otel-collector-config.yaml
└── grafana/
    ├── provisioning/
    │   ├── dashboards/
    │   │   └── dashboard.yml
    │   └── datasources/
    │       └── prometheus.yml
    └── dashboards/
        └── pedegas-metrics.json
```

