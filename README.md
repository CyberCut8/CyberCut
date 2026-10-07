--======================================================================================================================--
--                                      FLY GUI V3 PREMIUM REMASTERED (BY CYBERPUNKER)                                  --
--======================================================================================================================--
local main = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local up = Instance.new("TextButton")
local down = Instance.new("TextButton")
local onof = Instance.new("TextButton")
local TextLabel = Instance.new("TextLabel")
local plus = Instance.new("TextButton")
local speed = Instance.new("TextLabel")
local mine = Instance.new("TextButton")
local closebutton = Instance.new("TextButton")
local mini = Instance.new("TextButton")
local creditLabel = Instance.new("TextLabel")

-- Меню выбора стран и языков
local langButton = Instance.new("TextButton")
local LangFrame = Instance.new("Frame")
local LangScroll = Instance.new("ScrollingFrame")
local LangSearch = Instance.new("TextBox")

-- Полная база локализации под интерфейс
local Translations = {
	["Russia"] = {Title = "ПОЛЕТ V3", Up = "ВВЕРХ", Down = "ВНИЗ", Fly = "вкл", Credit = "Создано группой Киберпункер"},
	["USA"] = {Title = "FLY GUI V3", Up = "UP", Down = "DOWN", Fly = "fly", Credit = "By Cyberpunker"},
	["China"] = {Title = "飞行 V3", Up = "向上", Down = "向下", Fly = "开启", Credit = "由 Cyberpunker 团队创建"},
	["Germany"] = {Title = "FLIEGEN V3", Up = "HOCH", Down = "RUNTER", Fly = "ein", Credit = "Von Cyberpunker-Gruppe"},
	["France"] = {Title = "VOL GUI V3", Up = "HAUT", Down = "BAS", Fly = "on", Credit = "Par le groupe Cyberpunker"},
	["Japan"] = {Title = "飛行 V3", Up = "上昇", Down = "下降", Fly = "有効", Credit = "Cyberpunker グループ作成"},
	["Ukraine"] = {Title = "ПОЛІТ V3", Up = "ВГОРУ", Down = "ВНИЗ", Fly = "увімк", Credit = "Створено групою Кіберпункер"},
	["Kazakhstan"] = {Title = "ҰШУ V3", Up = "ЖОҒАРЫ", Down = "ТӨМЕН", Fly = "қосу", Credit = "Киберпункер тобы жасаған"}
}
local Countries = {"Russia", "USA", "China", "Germany", "France", "Japan", "Ukraine", "Kazakhstan"}
for i = 1, 187 do table.insert(Countries, "Country_"..i) end

-- [ИНИЦИАЛИЗАЦИЯ КОРНЯ СИСТЕМЫ]
main.Name = "main"
main.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
main.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
main.ResetOnSpawn = false

-- [ГЛАВНАЯ СТЕЛКЯННАЯ ПАНЕЛЬ - ТОТ САМЫЙ ОФИГЕННЫЙ ДИЗАЙН]
Frame.Name = "MainFrame"
Frame.Parent = main
Frame.BackgroundColor3 = Color3.fromRGB(15, 20, 30)
Frame.BackgroundTransparency = 0.2
Frame.Position = UDim2.new(0.100320168, 0, 0.379746825, 0)
Frame.Size = UDim2.new(0, 260, 0, 160)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true
Frame.ClipsDescendants = true

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 16)
mainCorner.Parent = Frame

local mainStroke = Instance.new("UIStroke")
mainStroke.Thickness = 1.8
mainStroke.Color = Color3.fromRGB(0, 180, 255)
mainStroke.Transparency = 0.4
mainStroke.Parent = Frame

local TweenService = game:GetService("TweenService")
local tInfo = TweenInfo.new(0.3, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

-- Кастомная функция применения Glassmorphism-стилей
local function ApplyGlassStyle(element, isButton, backColor, textColor)
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 8)
    corner.Parent = element
    element.Font = Enum.Font.GothamMedium
    element.TextColor3 = textColor or Color3.fromRGB(255, 255, 255)
    
    if isButton then
        element.BackgroundColor3 = backColor
        element.BackgroundTransparency = 0.2
        element.AutoButtonColor = false
        element.MouseEnter:Connect(function()
            TweenService:Create(element, TweenInfo.new(0.18), {BackgroundTransparency = 0, TextColor3 = Color3.fromRGB(255, 255, 255)}):Play()
        end)
        element.MouseLeave:Connect(function()
            TweenService:Create(element, TweenInfo.new(0.18), {BackgroundTransparency = 0.2}):Play()
        end)
    else
        element.BackgroundColor3 = backColor
        element.BackgroundTransparency = 0.5
    end
end

-- [МОДЕРНИЗАЦИЯ И СТАТИЧЕСКАЯ РАССТАНОВКА ЭЛЕМЕНТОВ ИНТЕРФЕЙСА]
TextLabel.Parent = Frame
TextLabel.Position = UDim2.new(0, 10, 0, 10)
TextLabel.Size = UDim2.new(0, 140, 0, 26)
TextLabel.Text = "FLY GUI V3"
TextLabel.TextSize = 13
ApplyGlassStyle(TextLabel, false, Color3.fromRGB(30, 40, 55), Color3.fromRGB(0, 220, 255))

up.Name = "up"
up.Parent = Frame
up.Position = UDim2.new(0, 10, 0, 45)
up.Size = UDim2.new(0, 50, 0, 26)
up.Text = "UP"
up.TextSize = 12
ApplyGlassStyle(up, true, Color3.fromRGB(0, 200, 100))

down.Name = "down"
down.Parent = Frame
down.Position = UDim2.new(0, 10, 0, 75)
down.Size = UDim2.new(0, 50, 0, 26)
down.Text = "DOWN"
down.TextSize = 11
ApplyGlassStyle(down, true, Color3.fromRGB(220, 160, 0))

plus.Name = "plus"
plus.Parent = Frame
plus.Position = UDim2.new(0, 65, 0, 45)
plus.Size = UDim2.new(0, 45, 0, 26)
plus.Text = "+"
plus.TextSize = 16
ApplyGlassStyle(plus, true, Color3.fromRGB(80, 100, 255))

speed.Name = "speed"
speed.Parent = Frame
speed.Position = UDim2.new(0, 115, 0, 45)
speed.Size = UDim2.new(0, 45, 0, 26)
speed.Text = "1"
speed.TextSize = 14
ApplyGlassStyle(speed, false, Color3.fromRGB(255, 90, 0))

mine.Name = "mine"
mine.Parent = Frame
mine.Position = UDim2.new(0, 65, 0, 75)
mine.Size = UDim2.new(0, 45, 0, 26)
mine.Text = "-"
mine.TextSize = 16
ApplyGlassStyle(mine, true, Color3.fromRGB(100, 210, 200), Color3.fromRGB(0,0,0))

onof.Name = "onof"
onof.Parent = Frame
onof.Position = UDim2.new(0, 115, 0, 75)
onof.Size = UDim2.new(0, 45, 0, 26)
onof.Text = "fly"
onof.TextSize = 12
ApplyGlassStyle(onof, true, Color3.fromRGB(0, 130, 255))

-- Кнопка переключения языков глобальной карты стран
langButton.Name = "langButton"
langButton.Parent = Frame
langButton.Position = UDim2.new(0, 165, 0, 45)
langButton.Size = UDim2.new(0, 85, 0, 56)
langButton.Text = "🌐 ЯЗЫК\nLANG"
langButton.TextSize = 11
ApplyGlassStyle(langButton, true, Color3.fromRGB(40, 50, 70), Color3.fromRGB(200, 240, 255))

-- Кнопки контроля состояния окна (Фиксированные позиции)
closebutton.Name = "Close"
closebutton.Parent = Frame
closebutton.Size = UDim2.new(0, 26, 0, 26)
closebutton.Position = UDim2.new(1, -36, 0, 10)
closebutton.Text = "X"
closebutton.TextSize = 14
ApplyGlassStyle(closebutton, true, Color3.fromRGB(255, 60, 60))

mini.Name = "minimize"
mini.Parent = Frame
mini.Size = UDim2.new(0, 26, 0, 26)
mini.Position = UDim2.new(1, -66, 0, 10)
mini.Text = "—"
mini.TextSize = 12
ApplyGlassStyle(mini, true, Color3.fromRGB(140, 90, 210))

-- Кредиты разработчиков
creditLabel.Name = "CreditLabel"
creditLabel.Parent = Frame
creditLabel.Position = UDim2.new(0, 10, 1, -35)
creditLabel.Size = UDim2.new(1, -20, 0, 25)
creditLabel.Text = "Создано группой Киберпункер"
creditLabel.TextColor3 = Color3.fromRGB(140, 160, 180)
creditLabel.Font = Enum.Font.GothamBold
creditLabel.TextSize = 11
creditLabel.BackgroundTransparency = 1

-- Стеклянный фрейм скроллинга стран
LangFrame.Name = "LangFrame"
LangFrame.Parent = Frame
LangFrame.Size = UDim2.new(0, 180, 0, 140)
LangFrame.Position = UDim2.new(1, 10, 0, 0)
LangFrame.BackgroundColor3 = Color3.fromRGB(12, 16, 24)
LangFrame.BackgroundTransparency = 0.2
LangFrame.Visible = false
local lfCorner = Instance.new("UICorner", LangFrame) lfCorner.CornerRadius = UDim.new(0, 12)
local lfStroke = Instance.new("UIStroke", LangFrame) lfStroke.Color = Color3.fromRGB(0, 180, 255) lfStroke.Transparency = 0.5

LangSearch.Parent = LangFrame
LangSearch.Size = UDim2.new(1, -20, 0, 26)
LangSearch.Position = UDim2.new(0, 10, 0, 10)
LangSearch.PlaceholderText = "Search..."
LangSearch.Text = ""
ApplyGlassStyle(LangSearch, false, Color3.fromRGB(30, 35, 45))

LangScroll.Parent = LangFrame
LangScroll.Size = UDim2.new(1, -20, 1, -50)
LangScroll.Position = UDim2.new(0, 10, 0, 42)
LangScroll.BackgroundTransparency = 1
LangScroll.BorderSizePixel = 0
LangScroll.ScrollBarThickness = 2
local lsLayout = Instance.new("UIListLayout", LangScroll)

local function TranslateInterface(countryName)
	local langData = Translations[countryName]
	if langData then
		TextLabel.Text = langData.Title; up.Text = langData.Up; down.Text = langData.Down; onof.Text = langData.Fly; creditLabel.Text = langData.Credit
	else
		TextLabel.Text = "FLY GUI ("..string.sub(countryName,1,3)..")"; up.Text = "UP"; down.Text = "DOWN"; onof.Text = "FLY"; creditLabel.Text = "By Cyberpunker"
	end
end

local function BuildList(search)
	for _, c in pairs(LangScroll:GetChildren()) do if c:IsA("TextButton") then c:Destroy() end end
	for _, name in pairs(Countries) do
		if search == "" or string.find(string.lower(name), string.lower(search)) then
			local b = Instance.new("TextButton", LangScroll)
			b.Size = UDim2.new(1, 0, 0, 22)
			ApplyGlassStyle(b, true, Color3.fromRGB(35, 40, 50))
			b.Text = name
			b.MouseButton1Click:Connect(function()
				langButton.Text = "🌐 "..string.sub(name,1,6)
				TranslateInterface(name)
				LangFrame.Visible = false
			end)
		end
	end
end
BuildList("")
LangSearch:GetPropertyChangedSignal("Text"):Connect(function() BuildList(LangSearch.Text) end)
langButton.MouseButton1Click:Connect(function() LangFrame.Visible = not LangFrame.Visible end)

-- [НАДЕЖНАЯ СИСТЕМА УПРАВЛЕНИЯ ОКНОМ И ОТКРЫТИЯ ПОСЛЕ СВЕРТЫВАНИЯ]
local isMinimized = false
mini.MouseButton1Click:Connect(function()
    isMinimized = not isMinimized
    LangFrame.Visible = false
    if isMinimized then
        mini.Text = "➕"
        TweenService:Create(Frame, tInfo, {Size = UDim2.new(0, 260, 0, 46)}):Play()
        creditLabel.Visible = false
    else
        mini.Text = "—"
        TweenService:Create(Frame, tInfo, {Size = UDim2.new(0, 260, 0, 160)}):Play()
        task.delay(0.2, function() creditLabel.Visible = true end)
    end
end)

closebutton.MouseButton1Click:Connect(function()
    LangFrame.Visible = false
    TweenService:Create(Frame, tInfo, {Size = UDim2.new(0, 260, 0, 0), BackgroundTransparency = 1}):Play()
    task.wait(0.3)
    main:Destroy()
end)

-- ==================================================================== --
--          ИНТЕГРАЦИЯ ОРИГИНАЛЬНОЙ ДИНАМИКИ И КЛИП-ПОЛЁТА              --
-- ==================================================================== --
speeds = 1
local speaker = game:GetService("Players").LocalPlayer
nowe = false

local tpwalking = false
local tis
local dis

-- Управление удержанием кнопок высоты UP
up.MouseButton1Down:connect(function()
	tis = up.MouseEnter:connect(function()
		while tis do
			wait()
			if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
				game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,1,0)
			end
		end
	end)
end)

up.MouseLeave:connect(function()
	if tis then
		tis:Disconnect()
		tis = nil
	end
end)

-- Управление удержанием кнопок высоты DOWN
down.MouseButton1Down:connect(function()
	dis = down.MouseEnter:connect(function()
		while dis do
			wait()
			if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
				game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,-1,0)
			end
		end
	end)
end)

down.MouseLeave:connect(function()
	if dis then
		dis:Disconnect()
		dis = nil
	end
end)

-- Переключатель полёта на кнопке Fly
onof.MouseButton1Down:connect(function()
	if nowe == true then
		nowe = false
		local char = speaker.Character
		if char and char:FindFirstChild("Humanoid") then
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Climbing,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.FallingDown,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Flying,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Freefall,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.GettingUp,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Jumping,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Landed,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Physics,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Ragdoll,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Running,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics,true)
			char.Humanoid:SetStateEnabled(Enum.HumanoidStateType.Swimming,true)
			char.Humanoid:ChangeState(Enum.HumanoidStateType.RunningNoPhysics)
		end
	else 
		nowe = true
		for i = 1, speeds do
			spawn(function()
				local hb = game:GetService("RunService").Heartbeat	
				tpwalking = true
				local chr = game.Players.LocalPlayer.Character
				local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
				while tpwalking and hb:Wait() and chr and hum and hum.Parent do
					if hum.MoveDirection.Magnitude > 0 then
						chr:TranslateBy(hum.MoveDirection * 1.5) -- Принудительный импульс полёта вперед
					end
				end
			end)
		end
		
		local Char = game.Players.LocalPlayer.Character
		if Char then
			if Char:FindFirstChild("Animate") then Char.Animate.Disabled = true end
			local Hum = Char:FindFirstChildOfClass("Humanoid") or Char:FindFirstChildOfClass("AnimationController")
			if Hum then
				for i,v in next, Hum:GetPlayingAnimationTracks() do
					v:AdjustSpeed(0)
				end
				Hum:SetStateEnabled(Enum.HumanoidStateType.Climbing,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.FallingDown,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Flying,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Freefall,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.GettingUp,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Jumping,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Landed,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Physics,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.PlatformStanding,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Ragdoll,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Running,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.RunningNoPhysics,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Seated,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.StrafingNoPhysics,false)
				Hum:SetStateEnabled(Enum.HumanoidStateType.Swimming,false)
				Hum:ChangeState(Enum.HumanoidStateType.Swimming)
			end
		end
	end

	-- Контроллеры захвата вектора камеры
	local plr = game.Players.LocalPlayer
	if plr.Character and plr.Character:FindFirstChild("Humanoid") then
		local torso = plr.Character:FindFirstChild("Torso") or plr.Character:FindFirstChild("UpperTorso")
		if torso then
			local bg = Instance.new("BodyGyro", torso)
			bg.P = 9e4
			bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
			bg.cframe = torso.CFrame
			
			local bv = Instance.new("BodyVelocity", torso)
			bv.velocity = Vector3.new(0,0.1,0)
			bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
			
			if nowe == true then
				plr.Character.Humanoid.PlatformStand = true
			end
			
			while nowe == true do
				game:GetService("RunService").RenderStepped:Wait()
				local camCFrame = game.Workspace.CurrentCamera.CoordinateFrame
				local hum = plr.Character:FindFirstChild("Humanoid")
				
				if hum and hum.MoveDirection.Magnitude > 0 then
					bv.velocity = camCFrame.lookVector * (speeds * 25)
				else
					bv.velocity = Vector3.new(0, 0, 0)
				end
				bg.cframe = camCFrame
			end
			
			bg:Destroy()
			bv:Destroy()
			if plr.Character:FindFirstChild("Humanoid") then
				plr.Character.Humanoid.PlatformStand = false
			end
			if plr.Character:FindFirstChild("Animate") then
				plr.Character.Animate.Disabled = false
			end
			tpwalking = false
		end
	end
end)

-- Инкремент скорости +
plus.MouseButton1Down:connect(function()
	speeds = speeds + 1
	speed.Text = tostring(speeds)
	if nowe == true then
		tpwalking = false
		task.wait()
		tpwalking = true
		spawn(function()
			local hb = game:GetService("RunService").Heartbeat	
			local chr = game.Players.LocalPlayer.Character
			local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
			while tpwalking and hb:Wait() and chr and hum and hum.Parent do
				if hum.MoveDirection.Magnitude > 0 then
					chr:TranslateBy(hum.MoveDirection * (speeds * 0.2))
				end
			end
		end)
	end
end)

-- Декремент скорости -
mine.MouseButton1Down:connect(function()
	if speeds == 1 then
		speed.Text = "min 1"
		task.wait(1)
		speed.Text = tostring(speeds)
	else
		speeds = speeds - 1
		speed.Text = tostring(speeds)
		if nowe == true then
			tpwalking = false
			task.wait()
			tpwalking = true
			spawn(function()
				local hb = game:GetService("RunService").Heartbeat	
				local chr = game.Players.LocalPlayer.Character
				local hum = chr and chr:FindFirstChildWhichIsA("Humanoid")
				while tpwalking and hb:Wait() and chr and hum and hum.Parent do
					if hum.MoveDirection.Magnitude > 0 then
						chr:TranslateBy(hum.MoveDirection * (speeds * 0.2))
					end
				end
			end)
		end
	end
end)

game:GetService("Players").LocalPlayer.CharacterAdded:Connect(function(char)
	task.wait(0.7)
	local hum = char:FindFirstChild("Humanoid")
	if hum then hum.PlatformStand = false end
	if char:FindFirstChild("Animate") then char.Animate.Disabled = false end
end)

game:GetService("StarterGui"):SetCore("SendNotification", { 
	Title = "FLY GUI V6";
	Text = "Создано Киберпункер";
	Text = "Created by Cyberpunker";
	Icon = "rbxthumb://type=Asset&id=5107182114&w=150&h=150",
	Duration = 5
})
