# MongoDB Backup Exporter

A utility for exporting MongoDB collections to JSON or CSV format.

## Features

- Export collections from MongoDB to JSON or CSV format.
- Automatically handles output directories.
- Supports exporting all collections or specified ones.
- Provides stats about each collection before exporting.

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

     ```bash
     sudo apt-get install mongodb-database-tools
     ```

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
    output_dir='output_directory_path',  # Directory where output files will be saved; defaults to current working directory if None
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

## License

This project is licensed under the MIT License. See the LICENSE file for details.
```

This version clearly specifies the installation steps for `mongoexport` on both Windows and Linux, making it easier for users to follow.
