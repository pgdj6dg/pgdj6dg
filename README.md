local script = [[
local fruits = {
    "Bari Bari no Mi",
    "Bara Bara no Mi",
    "Buddha Buddha no Mi",
    "Chop Chop Fruit",
    "Dark Dark Fruit",
    "Diamond Fruit",
    "Flame Flame Fruit",
    "Gum Gum Fruit",
    "Ice Ice Fruit",
    "Light Light Fruit",
    "Magma Magma Fruit",
    "Mera Mera no Mi",
    "Mochi Mochi no Mi",
    "Nika Nika no Mi",
    "Quake Quake Fruit",
    "Rumble Rumble Fruit",
    "Shadow Shadow Fruit",
    "Smoke Smoke Fruit",
    "Snow Snow Fruit",
    "Spirit Spirit Fruit",
    "String String Fruit",
    "Suke Suke no Mi",
    "Tori Tori no Mi",
    "Venom Venom Fruit",
    "Yami Yami no Mi",
    "Zushi Zushi no Mi",
    "Boo Fruit",
    "Frog Fruit",
    "Dough Fruit",
    "Control Fruit",
    "Phoenix Fruit",
    "Kilo Kilo Fruit",
    "Rumble Fruit",
    "Barrier Fruit",
    "Bishop Fruit",
    "Blizzard Fruit",
    "Bounty Fruit",
    "Fist Fruit",
    "Guardian Fruit",
    "Kumo Kumo no Mi",
    "Rao Rao no Mi",
    "Tama Tama no Mi",
    "Tonkotsu no Mi",
    "Yuki Yuki no Mi",
    "Horo Horo no Mi",
    "Gura Gura no Mi",
    "Ope Ope no Mi",
    "Hito Hito no Mi",
    "Mizu Mizu no Mi",
    "Bara Bara no Mi",
    "Hana Hana no Mi",
    "Suna Suna no Mi",
    "Yoru Yoru no Mi",
    "Ito Ito no Mi",
    "Mero Mero no Mi",
    "Baku Baku no Mi",
    "Mochi Mochi no Mi",
    "Nomi Nomi no Mi",
    "Raki Raki no Mi",
    "Suke Suke no Mi",
    "Tori Tori no Mi",
    "Pika Pika no Mi",
    "Noro Noro no Mi",
    "Oshi Oshi no Mi",
    "Ryu Ryu no Mi",
    "Ushi Ushi no Mi",
    "Kizuna no Mi",
    "Gumo Gumo no Mi",
    "Paw Paw no Mi",
    "Yuki Yuki no Mi",
    "Hito Hito no Mi",
}

-- Function to spawn a fruit in the player's hand
local function spawnFruit(fruitName)
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()

     Check if the fruit exists in the list
    if table.find(fruits, fruitName) then
         Create the fruit instance (assuming fruits are tools)
        local fruit = Instance.new("Tool") 
        fruit.Name = fruitName
        fruit.Parent = character
        
        -- Create a handle for the tool
        local handle = Instance.new("Part") 
        handle.Size = Vector3.new(1, 1, 1) -- Adjust size as needed
        handle.Name = "Handle"
        handle.Parent = fruit
        
        -- Position the handle in the player's right hand
        handle.Position = character:WaitForChild("RightHand").Position
        fruit.Handle = handle -- Set the handle for the tool
        fruit:Activate() -- Activate the tool to equip it
    else
        warn("Fruit not found: " .. fruitName)
    end
end

-- Function to create the farming hub UI
local function createFarmingHub()
    local player = game.Players.LocalPlayer
    local screenGui = Instance.new("ScreenGui", player.PlayerGui)
    local frame = Instance.new("Frame", screenGui)
    frame.Size = UDim2.new(0, 300, 0, 400) -- Adjust height for more options
    frame.Position = UDim2.new(0.5, -150, 0.5, -200)

    -- Create buttons for each fruit
    local function createFruitButton(fruitName, position)
        local fruitButton = Instance.new("TextButton", frame)
        fruitButton.Size = UDim2.new(0, 200, 0, 30)
        fruitButton.Position = position
        fruitButton.Text = fruitName
        fruitButton.MouseButton1Click:Connect(function()
            spawnFruit(fruitName)
        end)
    end

    -- Create buttons for each fruit in the list
    for i, fruit in ipairs(fruits) do
        createFruitButton(fruit, UDim2.new(0.5, -100, 0, 50 + (i - 1) * 35))
    end

    -- Optional: Add a label to show the title
    local titleLabel = Instance.new("TextLabel", frame)
    titleLabel.Size = UDim2.new(0, 300, 0, 50)
    titleLabel.Position = UDim2.new(0, 0, 0, 0)
    titleLabel.Text = "Select a Fruit:"
    titleLabel.TextScaled = true
    titleLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
end

-- Run the function to create the farming hub
createFarmingHub()
]]

loadstring(script)()
