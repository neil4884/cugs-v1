# CUGS Ground Control Station (V1)

A python-based ground station CLI and GUI software for receiving data via Serial Interface.
This repo includes example CLI and GUI main files and included specifically made library for this type of usages.

## Preferences
In preferences file (your preferable formats listed above), there are serveral configurations you can edit.

1. `header` (string) specifies packet header which is consistent (identical) in all received data. It is used to cut packet strings. Supported type: string. Supported inputs: Any. *Can be empty*: if empty the parser will split payloads with `\n` (new line) character instead.
2. `delimiter` (string) specifies delimiter that separates each block of data. Supported type: string.
3. `is_save` (string) specifies whether you want to save file or not. Supported type: string. Supported arguments: `true` and `false`.
4. `file_name` (string) specifies file name which delimited file and raw file will be saved. Supported type: string.
5. `file_ext` (string) specifies file extension which delimited file will be saved. Supported type: string.
6. `data_format` (string) specifies how many data (automatic) to receive, which data to be used, which one comes first. Supported type: list of strings.
7. `map_engine` (string) specifies map engine to be used. Supported type: string. Supported arguments: `earth`, `map` and empty string.
8. `plot_engine` (string) specifies plot engine to be used. Supported type: string. Supported arguments: `pyqtgraph` and `qchart`.
9. `use_plot` (string) Supported type: dict with keys: `x` (string) and `y` (string). In `x`, supported type: string. In `y`, supported type: list of strings.
10. `state` (string) specifies which block of data is used as the payload software state. Supported type: string.
11. `main_ui` (string) specifies file path of the UI file.
12. `state` (string) specifies the column name of state. (still in development). Supported type: string.
13. `placeholder` (any) just a placeholder.
14. `main_ui` (string) file path of main window ui file. Supported type: string.

## Data Format

Edit/Add your preferences to file `data_format.txt` in any universal `json`, `toml`, `xml`, or `yaml` format file as you prefer. All formats are readible and automatically detected. For the ground control station serial interface receiver to function, you have to make a preferences with root parent: `data_format` containing one child of a list of strings representing data to get parsed.

#### Upcoming features
If `data_format` is not present, the file will be created automatically with size of the first serial string encountered.

## Libraries

In `data_handler`:

1. `lib_preferences_reader.py` manage preferences file with ability to read, write and change format of the preferences file.

2. `lib_file_class.py` creates and/or loads files, directory and subdirectory for reading, appending, writing, renewing files, or convert `dict` parsed data based on `data_format.txt` data guides.

3. `lib_gis.py` includes self-explainatory `Coordinate` dataclass and `Gis` class for calculating most GIS values, e.g., Arc Angle, Arc Length, Line of Sight.

4. `lib_qchart.py` is for interfacing and plotting QChart in QGraphicsView object. (**Currently not available**)

5. `lib_parse_data.py` is for parsing data as specified in `data_format.txt`. It includes basic functionality of converting raw delimited string to ordered dictionary of data with its according key, and reducing data `list` set to improve performance when plotting charts.

6. `lib_mqtt.py` is for usages with MQTT subscribing and publishing topics.

7. `lib_serial_tools` is for creating a serial manager object and a serial device logger object.

8. `lib_threading` initializes `QThread` object for working with passed `class`. Signal functionality is also implemented.

9. `lib_time` create a current-time and delta-time objects.
