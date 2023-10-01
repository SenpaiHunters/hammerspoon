Inside your config add the following lines.

The default hotkey is `control + b`

It looks like this

![Arc at 00 52 05 on 2023@2x](https://github.com/SenpaiHunters/hammerspoon/assets/103985728/4a867cb0-d0be-41fb-ac6b-77a124708713)


```lua
-- Battery config
-- Press control + b to show battery stats
-- Feel free to change the keybind
hs.hotkey.bind({'ctrl'}, 'B', function()
  local battery_report = "Battery Information:\n" ..
    "Percentage: " .. hs.battery.percentage() .. "%\n" ..
    "Cycles: " .. hs.battery.cycles() .. "\n" ..
    "Capacity: " .. hs.battery.capacity() .. "mAh\n" ..
    "Design Capacity: " .. hs.battery.designCapacity() .. "mAh\n" ..
    "Is Charging: " .. (hs.battery.isCharging() and "Yes" or "No") .. "\n"

  -- Check if the timeToEmpty function is available before using it
  if hs.battery.timeToEmpty then
    battery_report = battery_report ..
      "Time to Empty: " .. (hs.battery.timeToEmpty() or "N/A") .. " minutes\n"
  else
    battery_report = battery_report ..
      "Time to Empty: N/A\n"
  end2

  -- Check if the timeToFullCharge function is available before using it
  if hs.battery.timeToFullCharge then
    battery_report = battery_report ..
      "Time to Full Charge: " .. (hs.battery.timeToFullCharge() or "N/A") .. " minutes\n"
  else
    battery_report = battery_report ..
      "Time to Full Charge: N/A\n"
  end

  hs.alert(battery_report)
end)
```
