# virt-viewer-sh
___
# Virt Viewer, Arquivo de configuração e suas opções

Para conectar em uma máquina virtual usando Virt Viewer, pode-se usar um arquivo com extenção ".vv".
Por exemplo: `local.vv`

Para usar, basta clicar no arquivo e irá surgir a janela do Virt Viewer com a Máquina Virtual.  
Se for usar o arquivo via linha de comando, deverá usar o comando `remote-viewer`.  
Um exemplo, se seu arquivo estiver no diretório Downloads, o comando deve ser executado desta maneira:  

```bash
remote-viewer ~/Downloads/arquivo.vv
```

## Um exemplo para o arquivo de configuração do Virt Viewer:

```ini
[virt-viewer]
type=spice
host=127.0.0.1
port=5902
delete-this-file=0
fullscreen=0
```

Neste exemplo:
- `type=spice` indica que o protocolo SPICE será usado para acessar a console gráfica da VM.
- `host=127.0.0.1` especifica o endereço IP local da VM.
- `port=5902` define a porta para a conexão SPICE.
- `delete-this-file=0` indica que o arquivo não deve ser excluído após o uso.
- `fullscreen=0` significa que o Virt Viewer não iniciará em modo de tela cheia.

Você pode usar o seguinte comando para executar o Virt Viewer (Sem o arquivo) com base nestas informações fornecidas:

```bash
virt-viewer --connect "spice://127.0.0.1:5902"
```
___

## Um exemplo mais completo com várias opções de configuração para o Virt Viewer.

```ini
[virt-viewer]
type=spice
host=127.0.0.1
port=5902
delete-this-file=0
fullscreen=0
wait=1
reconnect=1
zoom=100
direct=0
attach=1
```

Aqui estão algumas explicações para cada opção:

- `type=spice`: Indica que o protocolo SPICE será usado para acessar a console gráfica da VM.
- `host=127.0.0.1`: Especifica o endereço IP local da VM.
- `port=5902`: Define a porta para a conexão SPICE.
- `delete-this-file=0`: O arquivo não será excluído após o uso.
- `fullscreen=0`: O Virt Viewer não iniciará em modo de tela cheia.
- `wait=1`: Aguarda até que a VM inicie antes de conectar à console.
- `reconnect=1`: Reconecta automaticamente à VM se ela for reiniciada.
- `zoom=100`: Nível de zoom da janela de exibição (100% neste caso).
- `direct=0`: Não tenta tunelar a console via SSH.
- `attach=1`: Usa um socket pré-conectado via libvirt (se possível).

Você pode usar o seguinte comando para executar o Virt Viewer (Sem o arquivo) com base nestas informações fornecidas:

```bash
virt-viewer --connect "spice://127.0.0.1:5902" --wait --reconnect --zoom=100 --direct --attach
```
___

### Existem outras configurações que você pode ajustar no arquivo de configuração do Virt Viewer.  

1. **`title`**: Define o título da janela do Virt Viewer. Isso pode ser útil para identificar diferentes VMs.

    Exemplo:
    ```ini
    title=Minha VM
    ```

2. **`toggle-fullscreen`**: Permite alternar entre modo de tela cheia e janela.

    Exemplo:
    ```ini
    toggle-fullscreen=Ctrl+Alt+F
    ```

3. **`release-cursor`**: Define uma tecla de atalho para liberar o cursor do Virt Viewer (útil quando em tela cheia).

    Exemplo:
    ```ini
    release-cursor=Ctrl+Alt+R
    ```

4. **`secure-channels`**: Controla quais canais de comunicação são usados para a conexão SPICE.

    Exemplo:
    ```ini
    secure-channels=main,inputs
    ```

Um comando completo (Sem o arquivo) com todas as opções fornecidas até agora:
>A opção `--title "Minha VM"` não é disponível via linha de comando

```bash
virt-viewer --connect "spice://127.0.0.1:5902" --wait --reconnect --zoom=100 --direct --attach --hotkeys=toggle-fullscreen=Ctrl+Alt+F,release-cursor=Ctrl+Alt+R
```

Este comando inclui todas as opções, como aguardar a inicialização da VM, reconectar automaticamente, definir o nível de zoom, evitar o túnel SSH e usar um socket pré-conectado via libvirt. O título da janela será "Minha VM", e você pode alternar para o modo de tela cheia com `Ctrl+Alt+F` e liberar o cursor com `Ctrl+Alt+R`.
___

#### Para mais informações, consultar `man virt-viewer` ou `virt-viewer --help`
