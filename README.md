# 🖥️ SDumont | Supercomputador Santos Dumont

## Comandos Úteis

### Listar jobs de um usuário com horário previsto de início

```powershell
squeue -u $USER --start
```

### Consultar status de um job específico

```powershell
squeue -j <JOB ID>
```

### Exibir informações detalhadas sobre um job

```powershell
scontrol show jobid <JOB ID> -dd
```

### Copiar arquivos e pastas de um local para outro

```powershell
rsync <ORIG> <DEST>
```

### Ir para root

```powershell
cd /prj/<project name>/<user>
```

### Cancelar um job

```powershell
scancel <JOB ID>
```

### Consultar tamanho de uma pasta

```powershell
du -sh <PATH>
```

### Copiar sem substituir arquivos já existentes

```powershell
rsync -a --ignore-existing <ORIG> <DEST>
```

### Executar ambiente em modo dinâmico

```powershell
salloc --nodes=1 -p nvidia_small -J configuracao

ou

salloc --nodes=1 -p sequana_gpu_shared -J configuracao --time=01:00:00
```

### Criar e ativar ambiente

```powershell
conda create --prefix /scratch/<project name>/<user>/conda-env python=3.8
or
conda env create -f environment.yml
```


```powershell
conda activate /scratch/<project name>/<user>/conda-env
conda 
```

## Informações Importantes

- `ntasks-per-node` e `ntasks` precisa ser igual ao número de nós da fila. Esses números podem ser conferidos [nesse link](https://sdumont.lncc.br/support_manual.php?pg=support#5)

- Caso utilize o PyTorch, usar a fila `sequana_gpu_shared`, uma vez que há incompatibilidade de versões de pacotes

- O dataset a ser utilizado precisa estar dentro de `SCRATCH`

</aside>

## Status

- **CA - CANCELLED:** O job foi explicitamente cancelado pelo usuário ou pelo administrador.
- **CD - COMPLETED:** O job foi terminou normalmente, finalizando todos os seus processos em todos os nós.
- **CG - COMPLETING:** O job está no processo de finalização. Alguns dos processos ainda podem estar em execução em um dos nós.
- **F - FAILED:** O job terminou com um código de saída diferente de zero, indicando falha na execução/finalização.
- **NF - NODE_FAIL:** O job terminou devido a uma falha em um ou mais nós.
- **PD - PENDING:** O job está aguardando em fila pela alocação/liberação de recursos.
- **R - RUNNING:** O job em execução.
- **TO - TIMEOUT:** O job foi terminado por ter alcançado o seu limite de tempo.