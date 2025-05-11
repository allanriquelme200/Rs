-- Criar a UI
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Button = Instance.new("TextButton")

ScreenGui.Parent = game.CoreGui
ScreenGui.Name = "AutoFarmUI"

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
Frame.Position = UDim2.new(0.1, 0, 0.1, 0)
Frame.Size = UDim2.new(0, 200, 0, 100)

Button.Parent = Frame
Button.Position = UDim2.new(0.1, 0, 0.2, 0)
Button.Size = UDim2.new(0.8, 0, 0.6, 0)
Button.Text = "Iniciar Auto Farm"
Button.BackgroundColor3 = Color3.new(0.3, 0.6, 0.3)

local farming = false

-- Função para simular o auto farm
function AutoFarm()
    while farming do
        -- Pegando o lixo
        local lixo = workspace:FindFirstChild("Lixo")
        if lixo then
            game.Players.LocalPlayer.Character:MoveTo(lixo.Position)
            wait(2) -- esperar o player pegar o lixo
        end

        -- Entregar o lixo
        local lixeira = workspace:FindFirstChild("Lixeira")
        if lixeira then
            game.Players.LocalPlayer.Character:MoveTo(lixeira.Position)
            wait(2) -- esperar o player entregar
        end

        wait(1) -- tempo entre ciclos
    end
end

Button.MouseButton1Click:Connect(function()
    farming = not farming
    Button.Text = farming and "Parar Auto Farm" or "Iniciar Auto Farm"
    if farming then
        AutoFarm()
    end
end)
