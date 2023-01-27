


import Foundation

class Island {
    var player: Player
    var resources: [Resource]
    var shelterBuilt: Bool
    var daysLeft: Int
    
    init() {
        player = Player()
        resources = [Resource]()
        shelterBuilt = false
        daysLeft = 14
    }
    
    func gatherResource(resource: Resource) {
        resources.append(resource)
    }
    
    func buildShelter() {
        if resources.count >= 10 {
            shelterBuilt = true
            resources.removeFirst(10)
        } else {
            print("Not enough resources to build shelter.")
        }
    }
    
    func update() {
        daysLeft -= 1
        player.hunger += 1
        player.thirst += 1
        
        if player.hunger > 10 || player.thirst > 10 {
            player.health -= 1
        }
        
        if daysLeft <= 0 {
            gameOver()
        }
    }
    
    func gameOver() {
        if shelterBuilt {
            print("You successfully escaped the island!")
        } else {
            print("You were unable to escape the island.")
        }
    }
}
