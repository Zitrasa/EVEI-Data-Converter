# EVEI-Data-Converter
The intended use of this project is converting [EVE Online](https://www.eveonline.com) SDE (Static Data Export), created by [FuzzWork](https://www.fuzzwork.co.uk/dump/latest/), to the format, conveniently usable by my EVEI project. Maybe, you will find it usable too. You can find examples of prepared CSVs in `prepared/` folder.

## Usage
Script is prepared in jupiter notebook. You can use it in any way your soul desires. Required files are listed in jupiter script and located in `resources/` folder.

Currently, script uses only [Pandas](https://pandas.pydata.org/) and [NumPy](https://numpy.org/) libraries.

## Format
Currently, script tracks, which items are in game (by their blueprints `published` field) and filter out all unusable items, means items, that don't take part in any blueprint and are not product of some blueprint. 

1. Items data (blueprints are not included) is in `prepared/item_data.csv`. For now, script doesn't use packaged volume of ships, but it will surely do soon.

    | Column     | Description |
    | ----------- | ----------- |
    | `ID`      | TypeID of the item |
    | `blueprintID`   | TypeID of the item blueprint        |
    | `volume` | Full one unit volume |
    | `name` | In-game name of this item |
    
2. Blueprints are stored separately in `prepared/blueprint_data.csv`.


    | Column     | Description |
    | ----------- | ----------- |
    | `ID`      | TypeID of the blueprint |
    | `materialsID`   | TypeIDs of the materials to manufacture this blueprint |
    | `quantities` | Quantities of the materials to manufacture this blueprint |
    | `manufactureTime` | Basic time to manufacture one run of the blueprint |
    | `timeResearchTime` | Basic time to research +1 time efficiency |
    | `materialResearchTime` | Basic time to research +1 material efficiency |
    | `copyTime` | Basic time to make 1 copy 1-run BPC |
    | `maxCopyRuns` | Maximum amount of runs, BPC can have |
    | `productID` | TypeID of blueprint product |
    | `productQuantity` | Quantity of manufactured products |
    | `materialsCount` | Length of the `materialsID` and `quantities` arrays |
    | `name` | In-game name of this blueprint |

3. Invention details are stored in `prepared/invention_data.csv`. Currently, script doesn't save probabilities of the invention, but it will surely do.

    | Column     | Description |
    | ----------- | ----------- |
    | `originID`      | TypeID of original blueprint |
    | `materialsID`   | TypeIDs of the materials to invent this blueprint |
    | `quantities` | Quantities of the materials to invent this blueprint |
    | `inventionTime` | Basic time to invent one blueprint |
    | `inventedID` | TypeID of invented blueprint |
    | `blueprintRuns` | Runs count of the invented blueprint |
    | `materialsCount` | Length of the `materialsID` and `quantities` arrays |
