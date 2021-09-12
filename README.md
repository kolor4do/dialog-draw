![sa-mp-011](https://user-images.githubusercontent.com/61595463/132748196-c0691215-202d-4907-9a3a-805c78c35b11.png)
# dialog-draw
Dialogs using textdraws whose coordinates were extremely well calculated and centered.

## Functions

```pawn
AddDialogDrawItem(playerid, const item[], color = -1);
ShowDialogDraw(playerid, dialogid, title[]);
SetDialogDrawPage(playerid, page);
HideDialogDraw(playerid, cancelselect = true);
```

## Callback
```pawn
public OnDialogDrawResponse(playerid, ddialogid, response, listitem)
```

## Optional definitions

```pawn
#define  DD_MAX_PAGES                 17
#define  DD_MAX_ITEMS_PER_PAGE        6
#define  DD_TEXT_COLOR                -1446714113
#define  DD_BOX_COLOR                 255
#define  DD_ITEM_BOX_COLOR            0x333333FF
#define  DD_SELECT_COLOR              0xFFFF00FF
```

## Example of use
```pawn
#include <dialog-draw>

#define DIALOG_WEAPONS 3

public OnPlayerCommandText(playerid, cmdtext[])
{
    if(!strcmp(cmdtext, "/weapon", true))
    {
        AddDialogDrawItem(playerid, "Golf Club");
        AddDialogDrawItem(playerid, "Grenade");
        AddDialogDrawItem(playerid, "9mm");
        AddDialogDrawItem(playerid, "Desert Eagle");
        AddDialogDrawItem(playerid, "Sawnoff Shotgun");
        AddDialogDrawItem(playerid, "Tec-9");
        AddDialogDrawItem(playerid, "Sniper Rifle");
        ShowDialogDraw(playerid, DIALOG_WEAPONS, "Select a weapon");
        return 1;
    }
    return 0;
}

public OnDialogDrawResponse(playerid, dialogid, response, listitem)
{
    if(dialogid == DIALOG_WEAPONS)
    {
        if(response)
        {
            switch(listitem)
            {
                case 0: GivePlayerWeapon(playerid, WEAPON_GOLFCLUB, 99999);
                case 1: GivePlayerWeapon(playerid, WEAPON_GRENADE, 99999);
                case 2: GivePlayerWeapon(playerid, WEAPON_COLT45, 99999);
                case 3: GivePlayerWeapon(playerid, WEAPON_DEAGLE, 99999);
                case 4: GivePlayerWeapon(playerid, WEAPON_SAWEDOFF, 99999);
                case 5: GivePlayerWeapon(playerid, WEAPON_TEC9, 99999);
                case 6: GivePlayerWeapon(playerid, WEAPON_SNIPER, 99999);
            }
        }
    }
}
```


