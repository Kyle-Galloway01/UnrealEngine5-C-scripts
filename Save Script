// Declare the necessary includes and namespaces
#include "MyCharacter.h"
#include "Kismet/GameplayStatics.h"
#include "SaveGame/MySaveGame.h"

// Create a function to handle the saving process
void AMyCharacter::SaveGame()
{
    // Get the current player controller
    APlayerController* PlayerController = UGameplayStatics::GetPlayerController(GetWorld(), 0);
    if (!PlayerController) return;

    // Get the player character's location
    FVector CharacterLocation = GetActorLocation();

    // Get the player character's health and XP
    float Health = GetHealth();
    int32 XP = GetXP();

    // Create a new save game object and set its values
    UMySaveGame* SaveGameInstance = Cast<UMySaveGame>(UGameplayStatics::CreateSaveGameObject(UMySaveGame::StaticClass()));
    SaveGameInstance->CharacterLocation = CharacterLocation;
    SaveGameInstance->Health = Health;
    SaveGameInstance->XP = XP;

    // Save the game
    UGameplayStatics::SaveGameToSlot(SaveGameInstance, TEXT("MySaveSlot"), 0);

    // Print a message to confirm the save
    GEngine->AddOnScreenDebugMessage(-1, 2.0f, FColor::Green, TEXT("Game saved!"));
}

// Create a function to handle the S key input
void AMyCharacter::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    // Bind the S key to the SaveGame function
    PlayerInputComponent->BindAction("SaveGame", IE_Pressed, this, &AMyCharacter::SaveGame);
}
