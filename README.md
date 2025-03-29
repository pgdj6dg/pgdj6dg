-- Blox Fruits Simulator Script (For Roblox Studio Only)
local ServerStorage = game:GetService("ServerStorage")
local Players = game:GetService("Players")

-- List of Blox Fruits (example)
local fruits = {
    "Ice", "Flame", "Dark", "Light", "Rubber",
    "Quake", "Human: Buddha", "String", "Bird: Phoenix",
    "Rumble", "Paw", "Gravity", "Dough", "Shadow",
    "Venom", "Control", "Spirit", "Dragon"
}

-- Players' permanent fruits (data store simulation)
local playerPermFruits = {}

-- Admin commands (only works if player name is in this list)
local admins = {"YourUsernameHere"} -- Replace with your Roblox username

-- Function to give a random fruit
local function giveRandomFruit(player)
    local randomFruit = fruits[math.random(1, #fruits)]
    player:SetAttribute("CurrentFruit", randomFruit)
    return randomFruit
end

-- Function to give a perm fruit
local function givePermFruit(player, fruitName)
    if not table.find(fruits, fruitName) then
        return false -- Fruit doesn't exist
    end
    
    if not playerPermFruits[player.UserId] then
        playerPermFruits[player.UserId] = {}
    end
    
    table.insert(playerPermFruits[player.UserId], fruitName)
    return true
end

-- Admin command handler
local function handleAdminCommand(player, command, args)
    if not table.find(admins, player.Name) then
        player:Kick("You are not an admin!")
        return
    end
    
    if command == "kick" then
        local target = Players:FindFirstChild(args[1])
        if target then
            target:Kick("Kicked by admin.")
        end
    elseif command == "teleport" then
        local target1 = Players:FindFirstChild(args[1])
        local target2 = Players:FindFirstChild(args[2])
        if target1 and target2 then
            target1.Character:MoveTo(target2.Character.HumanoidRootPart.Position)
        end
    elseif command == "fruitall" then
        for _, plr in ipairs(Players:GetPlayers()) do
            giveRandomFruit(plr)
        end
    end
end

-- RemoteEvent setup (for client-server communication)
local remoteEvent = Instance.new("RemoteEvent")
remoteEvent.Name = "FruitRemote"
remoteEvent.Parent = ServerStorage

remoteEvent.OnServerEvent:Connect(function(player, action, ...)
    if action == "GetFruit" then
        local fruit = giveRandomFruit(player)
        print(player.Name .. " received: " .. fruit)
    elseif action == "GetPermFruit" then
        local fruitName = ...
        local success = givePermFruit(player, fruitName)
        if success then
            print(player.Name .. " got PERM: " .. fruitName)
        end
    elseif action == "AdminCommand" then
        local cmd, args = ...
        handleAdminCommand(player, cmd, args)
    end
end)

print("Blox Fruits Simulator Loaded!")
