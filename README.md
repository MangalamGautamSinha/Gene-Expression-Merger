# Gene-Expression-Merger

This repository contains a script to merge gene expression data files (`augmented_star_gene_counts.tsv`) downloaded from the GDC portal. The script processes the files to retain only relevant columns and combines them into a single CSV file.

## Features
- Processes multiple `augmented_star_gene_counts.tsv` files.
- Retains only the following columns:
  - `gene_id`
  - `gene_name`
  - `fpkm_unstranded` (renamed to the filename for easy identification)
- Filters rows to include only `protein_coding` genes.
- Merges all processed files into a single CSV file.

## Getting Started

### Prerequisites
Ensure the following are installed:
- Python 3.8 or above
- Required Python libraries:
  - `pandas`
  - `functools`

Install the necessary libraries using:
```bash
pip install pandas
```

### Usage

1. **Input Folder**:
   - Place all `augmented_star_gene_counts.tsv` files in the `./Normal` folder (or update the `input_folder` variable to match your folder structure).

2. **Output File**:
   - The merged output file will be saved as `./merged_sheets/Normal_merged.csv`.
   - Update the `output_file_name` variable if a different file name or location is desired.

3. **Running the Script**:
   - Execute the script in a Python environment:
     ```bash
     python script_name.py
     ```
   - The script processes each file, logs progress, and merges data into a final CSV.

4. **File Structure**:
   - Example input folder:
     ```
     ./Normal/
         file1.tsv
         file2.tsv
         file3.tsv
     ```
   - Output file: `./merged_sheets/Normal_merged.csv`

### Output
- A merged CSV file containing:
  - `gene_id` and `gene_name` as common keys.
  - Columns for each file’s `fpkm_unstranded` data, named after the file.

## Example Output

| gene_id        | gene_name  | file1       | file2       | file3       |
|----------------|------------|-------------|-------------|-------------|
| ENSG000001     | GeneA      | 12.3        | 8.1         | 9.0         |
| ENSG000002     | GeneB      | 4.2         | 7.4         | 3.5         |

## Notes
- Files must have the expected structure and column names.
- Rows with `gene_type != protein_coding` are excluded during processing.
- The script uses an outer merge to include all genes present in any file.
