## NanoVNA V2 Plus4

- Based on NanoVNA V2 firmware release 20201013.
- Added remote touch support for navigating the Plus4 screen and menus from WinVNA:
- https://xrjunque.nom.es/swdownload#winvna

## What has been added:

- Starting at ui.cpp 236:
- 
static bool simulated_touch = false;    /*************************   XJ   *******************/
static int simulated_touch_x;
static int simulated_touch_y;

void ui_simulate_touch(int x, int y)  /*************************   XJ   *******************/
{
    simulated_touch_x = x;
    simulated_touch_y = y;
    simulated_touch = true;

    UIEvent evt;
    evt.button = UIEventButtons::Touch;

    evt.type = UIEventTypes::Down;
    UIHW::emitEvent(evt);

    evt.type = UIEventTypes::Up;
    UIHW::emitEvent(evt);
}
