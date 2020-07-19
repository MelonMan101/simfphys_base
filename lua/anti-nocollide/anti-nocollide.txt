local function CheckCollisions()
     local Vehicles = ents.FindByClass( "gmod_sent_vehicle_fphysics_base" )

     local function entity:HasCollisions()
          return self:IsCollisionEnabled()
     end

     local function entity:EnableCollision()
          self:EnableCollisions( 1 )
     end
     
     for _, Vehicle in ipairs( Vehicles )
          if not Vehicle:HasCollisions() and not Vehicle:GetOwner():IsAdmin() then
             Vehicle:EnableCollision()
          end
     end
end

hook.add( "Think", "CFC_COLLISIONS_BLOCKER", CheckCollisions )