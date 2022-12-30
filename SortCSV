import tkinter as tk
import tkinter.filedialog as filedialog
import tkinter.messagebox as messagebox
import csv

# Custom sorting function
def sort_data(data, sort_key, reverse=False):
    # Modify this function to implement the desired sorting algorithm
    return sorted(data, key=lambda x: x[sort_key], reverse=reverse)

# Function to load CSV file and sort the data
def load_and_sort_csv():
    # Open file dialog to select CSV file
    filepath = filedialog.askopenfilename(filetypes=[("CSV file", "*.csv")])
    if not filepath:
        return

    # Read CSV file and store the data in a list of dictionaries
    data = []
    with open(filepath) as f:
        reader = csv.DictReader(f)
        for row in reader:
            data.append(row)

    # Ask user for sort key and sort order
    sort_key = input("Enter sort key: ")
    reverse = input("Sort in reverse order (y/n)? ") == "y"

    # Sort the data
    sorted_data = sort_data(data, sort_key, reverse)

    # Ask user for output file format
    file_format = input("Enter output file format (csv/txt): ")
    if file_format == "csv":
        # Write sorted data to CSV file
        output_filepath = filedialog.asksaveasfilename(defaultextension=".csv", filetypes=[("CSV file", "*.csv")])
        with open(output_filepath, "w") as f:
            writer = csv.DictWriter(f, fieldnames=reader.fieldnames)
            writer.writeheader()
            writer.writerows(sorted_data)
    elif file_format == "txt":
        # Write sorted data to TXT file
        output_filepath = filedialog.asksaveasfilename(defaultextension=".txt", filetypes=[("Text file", "*.txt")])
        with open(output_filepath, "w") as f:
            for row in sorted_data:
                f.write(str(row) + "\n")
    else:
        messagebox.showerror("Error", "Invalid output file format")

# Create a tkinter window
root = tk.Tk()
root.title("CSV Sorter")

# Add a button to open the file dialog
button = tk.Button(root, text="Select CSV file", command=load_and_sort_csv)
button.pack()

# Run the tkinter event loop
root.mainloop()
