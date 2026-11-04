# DSH

Versão fixa `0.2.1-rc.5`. Papel: Executor. Não é primário. Não é secondmate.

O `bin/fm-spawn.sh` recusa o nome `dsh`. O processo sai no fim da tarefa. Esta versão não tem hook de fim de turno.

## Fatos

| Fato | Valor |
|---|---|
| Binário | `/root/dsh/run.sh` faz `exec` do `dsh`. O `comm` é `MainThread`. O argv contém `/root/dsh/app/node_modules/.bin/dsh`. |
| Versão | `0.2.1-rc.5`. Não suba o pino. |
| Launch | `DSH_PERMISSION_MODE=read-only /root/dsh/run.sh --profile headless --json "<ordem>"` |
| Modelo | Só o CLIProxy em `127.0.0.1:8317`. Perfil `headless`. |
| Permissão | `read-only` é o padrão do `run.sh`. Não dê escrita. |
| Marker | `FM_DSH_HARNESS=dsh` no `run.sh`. Vale só com o binário dsh na ancestralidade. |
| Exit | rc 0 fecha a tarefa. rc 130 é o SIGINT. O pid não fica. |
| Resume | `--session-id <id>` na mesma versão. |
| Provas | `docs/verification/runtime-backends.md` no PR 1330 do rz-do (Ticket feceff30). |
