# GP-HACKER
GPS OFICIAL
-- GP HACKER SUPREMO: GP GUN com Tiros - V1.5
-- Criado pelo Supremo Guerreiro GP!

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

-- Função pra criar a arma
function criarArma()
    local gun = Instance.new("Tool")
    gun.Name = "GP Gun Suprema Tiros"
    
    local handle = Instance.new("Part")
    handle.Name = "Handle"
    handle.Size = Vector3.new(1,1,3)
    handle.BrickColor = BrickColor.new("Bright red")
    handle.Parent = gun
    
    gun.RequiresHandle = true
    gun.GripForward = Vector3.new(0,0,-1)
    gun.GripPos = Vector3.new(0,0,0)
    gun.GripRight = Vector3.new(1,0,0)
    gun.GripUp = Vector3.new(0,1,0)

    -- Evento ao clicar
    gun.Activated:Connect(function()
        -- Efeito de disparo (local)
        local ray = Instance.new("Part")
        ray.Size = Vector3.new(0.2,0.2,50)
        ray.BrickColor = BrickColor.new("Bright yellow")
        ray.Anchored = true
        ray.CanCollide = false
        ray.CFrame = handle.CFrame * CFrame.new(0,0,-25)
        ray.Parent = workspace

        -- Som de disparo
        local sound = Instance.new("Sound", handle)
        sound.SoundId = "rbxassetid://2920959" -- Som de tiro simples
        sound:Play()

        -- Remove o raio depois de 0.2 segundos
        game:GetService("Debris"):AddItem(ray, 0.2)
    end)

    -- Entrega pro jogador
    gun.Parent = LocalPlayer.Backpack
end

-- Executa a criação
criarArma()

-- Mensagem de confirmação
game.StarterGui:SetCore("SendNotification", {
    Title = "GP HACKER!";
    Text = "GP GUN com Tiro criada!";
    Duration = 5;
})
