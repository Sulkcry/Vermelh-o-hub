-- Meu BrookHub (exemplo)
-- Feito por: Sulkcry

-- Mensagem de boas-vindas
game.StarterGui:SetCore("SendNotification", {
    Title = "BrookHub";
    Text = "Bem-vindo ao BrookHub por Sulkcry!";
    Duration = 5;
})

-- Criação de uma interface simples (ScreenGui com botão)
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local Button = Instance.new("TextButton")

ScreenGui.Name = "BrookHubUI"
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Position = UDim2.new(0.5, -100, 0.5, -50)
Frame.Size = UDim2.new(0, 200, 0, 100)
Frame.Active = true
Frame.Draggable = true

Button.Parent = Frame
Button.BackgroundColor3 = Color3.fromRGB(60, 120, 255)
Button.Position = UDim2.new(0.1, 0, 0.3, 0)
Button.Size = UDim2.new(0.8, 0, 0.4, 0)
Button.Font = Enum.Font.GothamBold
Button.Text = "Ganhar velocidade"
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextSize = 18

Button.MouseButton1Click:Connect(function()
    local char = game.Players.LocalPlayer.Character
    if char and char:FindFirstChildOfClass("Humanoid") then
        char:FindFirstChildOfClass("Humanoid").WalkSpeed = 100
        game.StarterGui:SetCore("SendNotification", {
            Title = "BrookHub";
            Text = "Agora você está mais rápido!";
            Duration = 3;
        })
    end
end)

-- Atalho para fechar o Hub com a tecla "X"
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.X then
        ScreenGui:Destroy()
    end
end)
