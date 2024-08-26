# tNet - Gamemode

* [User](#user)
* [Character](#character)
    * [Inventory](#character-inventory)
    * [Roles](#character-roles)
* [Groups](#groups)

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
```lua
-- Retorna o objeto do grupo
local group = tNet.GetGroupById(groupId)

-- Retorna os membros do grupo
local groupMembers = group:getMembers()
```