local Players = game:GetService("Players")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")

-- Criando a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "NatanHub"
screenGui.Parent = playerGui

-- Criando o Frame principal do hub
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 400, 0, 600)
mainFrame.Position = UDim2.new(0.5, -200, 0.5, -300)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
mainFrame.BorderSizePixel = 0
mainFrame.Parent = screenGui

-- Criando o cabeçalho do hub
local titleLabel = Instance.new("TextLabel")
titleLabel.Size = UDim2.new(0, 400, 0, 50)
titleLabel.Position = UDim2.new(0, 0, 0, 0)
titleLabel.Text = "Natan 1.30"
titleLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
titleLabel.Font = Enum.Font.SourceSansBold
titleLabel.TextSize = 30
titleLabel.Parent = mainFrame

-- Criando um botão para abrir/fechar o menu
local toggleButton = Instance.new("TextButton")
toggleButton.Size = UDim2.new(0, 200, 0, 50)
toggleButton.Position = UDim2.new(0.5, -100, 0, 60)
toggleButton.Text = "Abrir Menu"
toggleButton.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
toggleButton.Parent = mainFrame

-- Função para abrir/fechar o menu
local isOpen = false
local function toggleMenu()
    isOpen = not isOpen
    if isOpen then
        mainFrame.Size = UDim2.new(0, 400, 0, 600)
        toggleButton.Text = "Fechar Menu"
    else
        mainFrame.Size = UDim2.new(0, 400, 0, 50)
        toggleButton.Text = "Abrir Menu"
    end
end

toggleButton.MouseButton1Click:Connect(toggleMenu)

-- Funções de Teletransporte
local function tpBanco()
    local banco = game.Workspace:FindFirstChild("Banco")
    if banco then
        player.Character.HumanoidRootPart.CFrame = banco.CFrame
    end
end

local function tpBaseFinal()
    local baseFinal = game.Workspace:FindFirstChild("BaseFinal")
    if baseFinal then
        player.Character.HumanoidRootPart.CFrame = baseFinal.CFrame
    end
end

local function tpTesla()
    local tesla = game.Workspace:FindFirstChild("Tesla")
    if tesla then
        player.Character.HumanoidRootPart.CFrame = tesla.CFrame
    end
end

local function tpCastelo()
    local castelo = game.Workspace:FindFirstChild("Castelo")
    if castelo then
        player.Character.HumanoidRootPart.CFrame = castelo.CFrame
    end
end

-- Função NoClip
local noclipEnabled = false
local function toggleNoClip()
    noclipEnabled = not noclipEnabled
    local character = player.Character
    if character then
        for _, part in pairs(character:GetDescendants()) do
            if part:IsA("BasePart") then
                part.CanCollide = not noclipEnabled
            end
        end
    end
end

-- Botões de Teletransporte
local tpButtonBanco = Instance.new("TextButton")
tpButtonBanco.Size = UDim2.new(0, 200, 0, 40)
tpButtonBanco.Position = UDim2.new(0.5, -100, 0, 100)
tpButtonBanco.Text = "TP Banco do Trem"
tpButtonBanco.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
tpButtonBanco.Parent = mainFrame
tpButtonBanco.MouseButton1Click:Connect(tpBanco)

local tpButtonBaseFinal = Instance.new("TextButton")
tpButtonBaseFinal.Size = UDim2.new(0, 200, 0, 40)
tpButtonBaseFinal.Position = UDim2.new(0.5, -100, 0, 150)
tpButtonBaseFinal.Text = "TP Base Final"
tpButtonBaseFinal.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
tpButtonBaseFinal.Parent = mainFrame
tpButtonBaseFinal.MouseButton1Click:Connect(tpBaseFinal)

local tpButtonTesla = Instance.new("TextButton")
tpButtonTesla.Size = UDim2.new(0, 200, 0, 40)
tpButtonTesla.Position = UDim2.new(0.5, -100, 0, 200)
tpButtonTesla.Text = "TP Tesla"
tpButtonTesla.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
tpButtonTesla.Parent = mainFrame
tpButtonTesla.MouseButton1Click:Connect(tpTesla)

local tpButtonCastelo = Instance.new("TextButton")
tpButtonCastelo.Size = UDim2.new(0, 200, 0, 40)
tpButtonCastelo.Position = UDim2.new(0.5, -100, 0, 250)
tpButtonCastelo.Text = "TP Castelo"
tpButtonCastelo.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
tpButtonCastelo.Parent = mainFrame
tpButtonCastelo.MouseButton1Click:Connect(tpCastelo)

-- Botão NoClip
local noclipButton = Instance.new("TextButton")
noclipButton.Size = UDim2.new(0, 200, 0, 40)
noclipButton.Position = UDim2.new(0.5, -100, 0, 300)
noclipButton.Text = "Toggle NoClip"
noclipButton.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
noclipButton.Parent = mainFrame
noclipButton.MouseButton1Click:Connect(toggleNoClip)

-- Estilo dos botões
local function styleButtons(button)
    button.MouseEnter:Connect(function()
        button.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
    end)
    button.MouseLeave:Connect(function()
        button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
    end)
end

styleButtons(tpButtonBanco)
styleButtons(tpButtonBaseFinal)
styleButtons(tpButtonTesla)
styleButtons(tpButtonCastelo)
styleButtons(noclipButton)
