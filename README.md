# tNet - Gamemode

* [User](#user)
* [Character](#character)
    * [Inventory](#character-inventory)
    * [Roles](#character-roles)
* [Groups](#groups)
* [Admin Commands](#admin-commands)

## User
```lua
-- Retorna o id do usuário através da source do jogador
tNet.GetUserIdByPlayerSrc(playerSrc)
```
Formas para obter o objeto do usuário:
```lua
-- Através do id do usuário
tNet.GetUserById(userId)
-- Através do source do jogador
tNet.GetUserByPlayerSrc(playerSrc)
-- Através do personagem ativo
tNet.GetUserByCharacterId(characterId)
```
`tNet.GetUsers()` Retorna uma tabela contendo o objeto de todos os usuários ativos no servidor.
## Character
```lua
-- Retorna o id do personagem através da source do jogador
tNet.GetCharacterIdByPlayerSrc(playerSrc)
```
Formas para obter o objeto do personagem:
```lua
-- Através do id do personagem
tNet.GetCharacterById(characterId)

-- Através do source do jogador
tNet.GetCharacterByPlayerSrc(playerSrc)
```
`tNet.GetCharacters()` Retorna uma tabela contendo o objeto de todos os personagens ativos no servidor.
```lua
-- Formas para obter o nome do personagem:
character:getName() -- Nome completo (first and last name)
character:getFirstName() -- Primeiro nome
character:getLastName() -- Sobrenome
```
## Character Inventory
```lua
character:getInventory()
character:getInventoryItem(itemName, metadata)
character:addInventoryItem(itemName, count, metadata, slot)
character:removeInventoryItem(itemName, count, metadata, slot)
character:setInventoryItem(itemName, count, metadata)
character:canCarryItem(itemName, count, metadata)
character:hasItem(itemName, metadata)
character:clearInventory()
character:getWeight()
character:getMaxWeight()
character:setMaxWeight(newWeight)
```
## Character Roles
```lua
-- Retorna os cargos atribuídos ao personagem.
local roles = character:getRoles()
--[[
    [
        {
            "label": "Chefe de Polícia",
            "groupId": 1,
            "id": 1,
            "rank": 1,
        }
    ]
]]

-- Atribuí cargo ao personagem.
character:addRole(roleId)

-- Remove cargo do personagem.
character:removeRole(roleId)

-- Atualiza a hierarquia do cargo do persoangem.
character:updateRoleRank(currentRoleRank, newRoleRank)
```

## Groups
Formas para obter o objeto do grupo:
```lua
-- Através do id do grupo
tNet.GetGroupById(groupId)
-- Através do nome (interno) do grupo
tNet.GetGroupByName(groupName) -- (ex: police, medical, etc...)
```

## Admin Commands
- **/selector** - Abre a seleção de personagem;
- **/paineladmin** - Painel administrativo
- **/nc** - Noclip;
- **/tp** `opcional: id do jogador/x, y, z` - Teletransporte (o tpway não existe, é só marcar no mapa e usar esse comando sem argumentos);
- **/tptome** `id do jogador` - Puxar jogador;
- **/cds** - Copiar coordenadas (É salvo na sua área de transferência - vec4);
- **/car** `modelo do veículo` - Spawnar um veículo;
- **/dv** `opcional: raio` - Deletar veículo(s);
- **/revive** `opcional: id do jogador` - Reviver jogador morto (Se não existir argumentos o comando será aplicado no seu ped);
- **/fix** - Conserta o veículo que o ped está dentro e fora - próximo e olhando para o veículo;
- **/clean** - Limpa o veículo que o ped está dentro e fora - próximo e olhando para o veículo;
- **/tunning** - Aplica melhorias no máximo no veículo que o ped está dentro e fora - próximo e olhando para o veículo;
- **/addwl** `id do jogador` - Adiciona jogador na lista de permissões de entrada no servidor;
### Inventário
- **/additem ou /giveitem** `id do jogador` `nome do item` `quantidade` `opcional: metadata` - Dá um item a um jogador com o id fornecido;
- **/removeitem** `id do jogador` `nome do item` `quantidade` `opcional: metadata` - Remove um item para um jogador com o id fornecido;
- **/setitem** `id do jogador` `nome do item` `quantidade` `opcional: metadata` - Define a contagem de itens para um jogador, removendo ou adicionando conforme necessário;
- **/clearevidence** `id do armário a ser limpo` - Limpa um armário de evidências policiais com a identificação fornecida;
- **/takeinv** `id do jogador` - Confisca o inventário de destino para restaurar com /restoreinv;
- **/restoreinv ou /returninv** `id do jogador` - Restaura um inventário previamente confiscado para o jogador;
- **/clearinv** `id do inventário/player` - Limpa todos os itens do inventário;
- **/saveinv** `opcional: lock (true/false) | default: false` (Bloqueia o acesso ao inventário até reiniciar ou salva sem bloqueio) - Salva todas as alterações de inventário pendentes no banco de dados;
- **/viewinv** `id do inventário/player` - Inspeciona o inventário de destino (não permite interações);