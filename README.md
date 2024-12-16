-- Pets Go Script for Delta Executor (Mobile Users)

-- Function to Auto-Collect Coins
local function autoCollectCoins()
    local player = game.Players.LocalPlayer
    local coinFolder = workspace:FindFirstChild("Coins")
    if coinFolder then
        for _, coin in pairs(coinFolder:GetChildren()) do
            if coin:IsA("BasePart") then
                firetouchinterest(player.Character.HumanoidRootPart, coin, 0)
                firetouchinterest(player.Character.HumanoidRootPart, coin, 1)
            end
        end
    end
end

-- Enable 2x Luck
local function enableDoubleLuck()
    local luckEvent = game.ReplicatedStorage:FindFirstChild("LuckMultiplierEvent")
    if luckEvent then
        luckEvent:FireServer(2) -- Enabling 2x Luck
        print("2x Luck Enabled!")
    else
        print("LuckMultiplierEvent not found.")
    end
end

-- Main loop to keep the features running
while true do
    pcall(autoCollectCoins) -- Collect coins automatically
    pcall(enableDoubleLuck) -- Enable 2x Luck
    wait(5) -- Adjust this wait to prevent detection or being too fast
end
