-- Script para Auto Farm no Roblox (server-side)
local player = game.Players.LocalPlayer
local autoFarmEnabled = false  -- Flag para verificar se o auto farm está ativado

-- Função que ativa/desativa o Auto Farm
local function toggleAutoFarm()
    autoFarmEnabled = not autoFarmEnabled
    if autoFarmEnabled then
        print("Auto Farm ativado!")
    else
        print("Auto Farm desativado!")
    end
end

-- Simula a coleta de recursos (Exemplo: Moedas)
local function autoCollectResources()
    while autoFarmEnabled do
        wait(1)  -- Espera 1 segundo entre as ações de coleta
        -- Lógica para coleta de recursos, ex: adicionar moeda ao jogador
        -- Aqui você pode colocar a lógica que corresponde ao seu jogo
        print("Coletando recursos...")
        -- Exemplo fictício: player.Coins = player.Coins + 1 (Aumentando a quantidade de moedas)
    end
end

-- Escuta os comandos para ativar ou desativar o auto farm
game:GetService("ReplicatedStorage").OnServerEvent:Connect(function(player, command)
    if command == "ativar" then
        toggleAutoFarm()
        if autoFarmEnabled then
            autoCollectResources()
        end
    elseif command == "desativar" then
        toggleAutoFarm()
    end
end)
