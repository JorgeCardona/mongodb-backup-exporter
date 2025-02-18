# MongoDB Backup Exporter
A utility for exporting MongoDB collections to JSON or CSV format.

[![Publish MongoDB Backup Collections Exporter Python Package](https://github.com/JorgeCardona/mongodb-backup-exporter/actions/workflows/python-publish.yml/badge.svg)](https://github.com/JorgeCardona/mongodb-backup-exporter/actions/workflows/python-publish.yml)

## Features

- Export collections from MongoDB to JSON or CSV format.
- Automatically handles output directories.
- Supports exporting all collections or specified ones.
- Provides stats about each collection before exporting.
- Supports pretty-printing of JSON output and exporting JSON in list format.

## Installation PyPI

You can install `mongodb-backup-exporter` directly from PyPI using pip:

```bash
pip install mongodb-backup-exporter
```

## Installation Using Repository 

1. **Clone the repository**:

   ```bash
   git clone https://github.com/jorgecardona/mongodb-backup-exporter.git
   cd mongodb-backup-exporter
   ```

2. **Install required Python packages**:

   Create a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

   Then, install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

3. **Install `mongoexport` from MongoDB Command Line Database Tools Download**:

   - **Windows**: Download the MongoDB Database Tools from the [MongoDB official site](https://www.mongodb.com/try/download/database-tools). After installation, ensure that the `mongoexport` executable is in your system's PATH.

   - **Linux**: You can install the MongoDB Database Tools using the package manager for your distribution. For example, on Ubuntu, you can do:

   # Validate Linux Version
     ```bash
     uname -a
     ```

     ```bash
     cat /etc/os-release
     ```
   ![linux_version](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/linux_version.png)

   # Install mongodb-database-tools

     ```bash
     curl -O https://fastdl.mongodb.org/tools/db/mongodb-database-tools-debian12-x86_64-100.10.0.tgz && \
      tar -xvzf mongodb-database-tools-debian12-x86_64-100.10.0.tgz && \
      cd mongodb-database-tools-debian12-x86_64-100.10.0 && \
      sudo cp -r bin/* /usr/local/bin/ && \
      cd .. && \
      rm -rf mongodb-database-tools-debian12-x86_64-100.10.0 && \
      rm mongodb-database-tools-debian12-x86_64-100.10.0.tgz
     ```

   # Verify the version of MongoDB Database Tools
     ```bash
     mongoexport --version
     ```

   # Check the installation directory for MongoDB Database Tools
     ```bash
     which mongoexport
     ```

   ![install_mongodb-database-tools](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/install_mongodb-database-tools.png)

     Alternatively, you can download the tools from the [MongoDB official site](https://www.mongodb.com/try/download/database-tools/).

## Usage

To use the `MongoDBBackupExporter`, you can instantiate it in your script:

```python
from mongodb_backup_exporter import MongoDBBackupExporter

# Configuration for MongoDB connection
username = "your_username"  # MongoDB username
password = "your_password"  # MongoDB password
hostname = "your_cluster.mongodb.net"  # MongoDB cluster address
db_name = "your_database_name"  # Database name
mongoexport_path = "path/to/mongoexport"  # Path to mongoexport executable

# Create an instance of MongoDBBackupExporter
exporter = MongoDBBackupExporter(
    username=username,  # The username for the MongoDB database
    password=password,  # The password for the MongoDB database
    hostname=hostname,  # The cluster address for the MongoDB connection
    db_name=db_name,  # The name of the database to be backed up
    mongoexport_path=mongoexport_path,  # Path to the mongoexport executable
    output_format='json',  # Specifies the format for the exported files; can be 'json' or 'csv'
    json_list=True,  # If True, each JSON object will be written on a new line in list format
    pretty_json=True,  # If True, the JSON output will be formatted for better readability
    output_dir='output_directory_path',  # Directory where output files will be saved; defaults to current working directory if None
    collections_to_export=['collection1', 'collection2'],  # Specify collections to export; if None, all collections will be exported
)

# Execute the export process
# This method will export the specified collections from the MongoDB database
# to the designated output directory in the specified format.
exporter.execute_export()
```

## Requirements

- Python 3.6 or higher
- `pymongo` library (install via `pip install pymongo`)
- `mongoexport` must be installed and accessible in your system's PATH.

# Extracts to Json 
![mongo_db_json](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongo_db_json.png)

# Extracts to CSV 
![mongo_db_csv](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongo_db_csv.png)

# Extracts to Json List
![mongo_db_json_list](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongo_db_json_list.png)

# Extracts to Json Pretty
![mongo_db_json_pretty](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongo_db_json_pretty.png)

# Restore Collection Using Json file
![mongodb_restore_1](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongodb_restore_1.png)
![mongodb_restore_2](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongodb_restore_2.png)
![mongodb_restore_3](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongodb_restore_3.png)
![mongodb_restore_4](https://raw.githubusercontent.com/JorgeCardona/mongodb-backup-exporter/refs/heads/main/images/mongodb_restore_4.png)

## License

This project is licensed under the MIT License. See the LICENSE file for details.