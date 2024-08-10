# Power Automate Workflow for Converting Specific Files to PDF

This project provides a detailed guide on creating a Power Automate workflow that converts specific files from a SharePoint document library into PDF format. Files are automatically detected, converted, and saved to the desired location.

## How It Works

1. Trigger File Creation: The first step is adding the "When a file is created (properties only)" trigger in SharePoint. This trigger initiates the workflow whenever a new file is created.
2. Retrieve File Content: Next, the "Get file content" action is added in SharePoint, which retrieves the content of the file.
3. Process File Name: A "Compose" action is added, where the file name is set as "File_Name." The input for this action is "File Name with extension." This ensures the file name is processed correctly in the following steps.
4. Add Condition: A "Condition" action is added with the following formula:

```plaintext
if(
    or(
        endsWith(outputs('File_Name'), '.docx'),
        endsWith(outputs('File_Name'), '.doc'),
        endsWith(outputs('File_Name'), '.png'),
        endsWith(outputs('File_Name'), '.jpg')
    ),
    true,
    false
)
```
If the content evaluates to true, the workflow proceeds.

5. Create File: The "Create file" action in OneDrive is added, allowing users to specify where the files should be saved.
6. Convert to PDF: The "Convert file" action in OneDrive is used to convert the file to PDF format.
7. Save PDF File: The "Create file" action in OneDrive is used again to save the new PDF file. This action is renamed as shown in the image to "Create file for new Pdf file."
8. Save File to SharePoint: The "Create file" action in SharePoint is added and renamed as "Create file in SP," as seen in the image.
9. Delete Temporary Files: In the final step of the workflow, temporary files created in OneDrive are deleted to prevent unnecessary clutter.

![Convert_PDF](https://github.com/korhanh/Power-Automate-Workflow-for-Converting-Specific-Files-to-PDF/blob/main/convert_pdf.png)

## Features

- Automatic Conversion: Files in SharePoint are automatically converted to PDF format.
- Flexible Saving Options: Files can be saved between OneDrive and SharePoint as needed.
- Conditional Processing: File conversion is performed based on file type.
- Easy Integration: Seamlessly integrates into Power Automate workflows.
  
## Requirements

- Microsoft Power Automate subscription
- Basic knowledge of creating Power Automate flows
  
## Getting Started

- Import the provided template into your Power Automate flow.
- Adjust the data and saving settings according to your needs.
- Complete the flow and enable PDF conversion.

## Contributions and Feedback

Contributions to this project are welcome! If you encounter any issues or have suggestions for improvement, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](https://github.com/korhanh/Power-Automate-Workflow-for-Converting-Specific-Files-to-PDF/blob/main/LICENSE).

Feel free to use, modify, and distribute this project according to the terms specified in the license.

## Credits

This project is created and maintained by [korhanh]([link_to_your_github_profile](https://github.com/korhanh)).

If you use this project or find it helpful, consider giving it a star on GitHub!

Happy automating! :rocket:
