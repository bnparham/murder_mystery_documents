# **Project Idea**
A murder occurred on October 19, 2023, in Velenjak.  
You are in the role of a police workshop tasked with identifying the identity of the killer.
The game, developed in Persian, incorporates various parts of the city of Tehran that contain information stored in the municipality's database.

This addition highlights that the game is specifically designed for Persian-speaking users!

## Visit the Murder Mystery Project
[Project Link](https://murder-mystery.liara.run/)


# **Gameplay**

The story of the game takes place in the city of Tehran. There are various parts of the city that contain information stored in the municipality's database.

-   Security cameras hold the license plate numbers of vehicles that were on the streets in the game on a specific date.
    
-   The bank's payment portal contains the account numbers of individuals who were engaged in financial transactions on a specific date.
    
-   Mobile phones contain the phone numbers of the caller, recipient, and the duration of calls made on a specific date.

According to the project's ER diagram, you can see the complete number of centers in the next slide. You must identify the identities of the individuals associated with the information obtained from these centers (for example, which person is associated with the discovered license plate number or phone number?) and then, by compiling the information of the suspects, identify the person who appears in all of them as the killer.

![ERD diagram](https://s8.uupload.ir/files/erd_0714.jpg)

## API Endpoints

The backend exposes the following API endpoints:

- `api/person/`: Information about individuals involved in the mystery.
- `api/phone-calls/`: Details of phone calls related to the investigation.
- `api/location/`: Data on different locations relevant to the case.
- `api/street/`: Street-related information.
- `api/bank-account/`: Bank account details.
- `api/atm/`: Information related to ATMs.
- `api/security-log/`: Security log records.
- `api/crime-scene/`: Details about the crime scene.
- `api/item/`: Items associated with the investigation.
- `api/clue/`: Clues that might help solve the mystery.
- `api/airports/`: Airport details.
- `api/flights/`: Information about flights.
- `api/passengers/`: Passenger details.
- `api/interviews/`: Records of interviews conducted during the investigation.

Additionally, there is a special endpoint for playing Tic-Tac-Toe with AI:


## Tic-Tac-Toe
**This feature utilizes the Min-Max AI algorithm, and I have developed an API endpoint using Django Rest Framework (DRF) to support it.**

> 💡**The documentation regarding the communication between the Min-Max
> algorithm and the API, as well as the compression or extraction of
> data, is exclusive to this project.**



### Tic-Tac-Toe Endpoints

#### `GET /tictoc/list`
View logs of player status on the Tic-Tac-Toe board.

#### `POST /tictoc/startnewgame`
Start a new Tic-Tac-Toe game (send empty json body)

Initial State Response:
```json
{
    "id": "?",
    "player": "X",
    "action": null,
    "board": "000000000",
    "winner": null,
    "terminal": false,
    "time": "?"
}
```
#### `POST /tictoc/moveapi`
Make a move on the Tic-Tac-Toe board.
we should send data to this endpoint like :
```json
{
	"letter":"X",
	"action":"01"
}
```
letter: The player's turn, which can be "X" or "O".

action: The player's choice of section on the board, where the first digit represents the row index, and the second digit represents the column index.


## XO app : Logic of Action

The action value in the Tic-Tac-Toe move represents the player's choice of section on the board. The format of the action is a two-digit string, where the first digit represents the row index, and the second digit represents the column index.

For example:

action: "01" corresponds to the cell in the first row and second column.
action: "22" corresponds to the cell in the third row and third column.

## XO app : Game Termination and Winner Determination
If the terminal field is True, the game is finished.

If the winner field is null, the game is a draw (equal).

If the winner field is equal to 'X', then 'X' wins.

If the winner field is equal to 'O', then 'O' wins.