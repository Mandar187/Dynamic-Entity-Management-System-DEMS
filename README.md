# 🚗 Dynamic-Entity-Management-System-DEMS

A high-performance, hybrid system for Unreal Engine that dynamically despawns distant actors (like vehicles or NPCs), simulates them using CPU-side logic with structs, and respawns them using actor pooling as they approach the player. Perfect for open-world, large-scale, or mobile-optimized games 🎮✨

---

## 💡 Key Features

- ✅ **Distance-based Actor Handling**  
  Automatically despawn actors when far from the player and restore them as they return.

- 🧠 **CPU-side Simulation with Structs**  
  Maintain logical state (movement, AI, fuel, etc.) in lightweight `FStructData`.

- 🔁 **Actor Pooling**  
  Reuses hidden actors instead of spawning/destroying – saves CPU, GPU, and memory.

- 🔥 **Modular & Scalable**  
  Works for cars, NPCs, wildlife, loot, zombies – you name it.

---

## 🧪 Use Cases

- Open-world traffic systems (like GTA-style)
- Wildlife roaming systems
- Background AI logic
- Optimized city life simulations
- Post-apocalyptic survivor roaming

---

## ⚙️ How It Works

1. **Actors Near Player**  
   ➤ Fully rendered and active in world.

2. **Actors Far From Player**  
   ➤ Saved as `FStoredVehicleData`  
   ➤ Simulated via logic-only CPU update  
   ➤ Actor is disabled or returned to pool

3. **Actors Re-Enter Range**  
   ➤ Pulled from pool  
   ➤ Re-initialized with saved data  
   ➤ Resumes behavior seamlessly

---

## 🛠️ System Components

| Name | Description |
|------|-------------|
| `FStoredVehicleData` | Struct that stores actor state (position, velocity, AI state, etc.) |
| `BP_VehicleManager` | Handles distance checks, spawning, and CPU-side simulation |
| `BP_Car` (or NPC) | Custom actor with `InitFromStruct()` for restoring state |
| `Object Pool` | Pool of reusable hidden actors |

---

