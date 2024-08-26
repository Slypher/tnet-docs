# tNet - Gamemode

* [Character](#character)
    * [Roles](#character-roles)
* [Groups](#groups)

## Character

Formas para obter o objeto do personagem:
```lua
-- Através do id do personagem
tNet.GetCharacterById(characterId)

-- Através do source do jogador
tNet.GetCharacterByPlayerSrc(playerSrc)
```
`tNet.GetCharacters()` Retorna uma tabela contendo o objeto de todos os personagens ativos no servidor.

## Character Roles
```lua
-- Retorna os cargos atribuídos ao personagem.
local roles = character.getRoles()
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
character.addRole(roleId)

-- Remove cargo do personagem.
character.removeRole(roleId)

-- Atualiza a hierarquia do cargo do persoangem.
character.updateRoleRank(currentRoleRank, newRoleRank)
```

## Groups
```lua
-- Retorna o objeto do grupo
local group = tNet.GetGroupById(groupId)

-- Retorna os membros do grupo
local groupMembers = group:getMembers()
```