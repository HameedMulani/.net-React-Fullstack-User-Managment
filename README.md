# Dotnet-React-Fullstack-User-Managment
## User Management System with Image Upload and Deletion

<!-- ## Overview: Gives a high-level overview of the project -->
## Overview
This project is a **.NET Core MVC** application designed to manage user profiles with image upload and deletion capabilities. It allows users to create, view, update, and delete profiles, with their associated profile pictures stored in the server's file system.

When a user is deleted, their profile picture is also removed from the server, ensuring efficient file management and cleanup.

<!-- ## Features: List out the main functionalities of the project -->
## Features
- **Add User**: Create new user profiles with personal information (e.g., name, contact details, and profile picture).
- **Delete User**: Remove a user from the database by their ID, and automatically delete their associated profile picture from the server.
- **Image Upload**: Profile pictures are uploaded and saved in the `/Images` folder, with unique file names generated using timestamps.
- **PostgreSQL Integration**: User data, including the path to their profile picture, is stored in a PostgreSQL database.
- **File Management**: Images are efficiently handled, ensuring that each file is unique and properly deleted when no longer needed.

<!-- ## Technology Stack: Summarizes the key technologies used in the project -->
## Technology Stack
- **Backend**: .NET Core MVC (C#)
- **Database**: PostgreSQL
- **File Handling**: FileStream for image uploads and deletion
- **ORM**: Entity Framework Core

<!-- ## API Endpoints: Provide details of the key API endpoints for users who want to interact with the project -->
## API Endpoints

### Add User
- **Endpoint**: `POST /api/users`
- **Description**: Adds a new user to the database along with an uploaded profile picture.
- **Request**: 
  - JSON data with user details
  - Image file

### Delete User
- **Endpoint**: `DELETE /api/users/{id}`
- **Description**: Deletes a user from the database by their ID and removes the associated image from the file system.

<!-- ## Example Code: Showing a code snippet related to one of the key features of the project, such as image deletion -->
### Example Code for Image Deletion
The following code snippet shows how an image is deleted from the server when the corresponding user is removed from the database:

```csharp
private void DeleteImageFromFileSystem(string imagePath)
{
    string correctedImagePath = imagePath.Replace("Image/", "").TrimStart('/');
    var fullImagePath = Path.Combine(Directory.GetCurrentDirectory(), "Images", correctedImagePath);

    if (File.Exists(fullImagePath))
    {
        File.Delete(fullImagePath);
    }
}
```

![image](https://github.com/user-attachments/assets/f0dec021-f4e5-46b9-8d3f-4949758b76c9)

![image](https://github.com/user-attachments/assets/45ff018b-5cc2-40c8-af29-5fe914cec636)

![image](https://github.com/user-attachments/assets/c3bca7c5-3f6d-436a-b91e-f8194aa11abd)

![image](https://github.com/user-attachments/assets/b81eea41-a8d1-41f4-8ca6-71de52549e72)

![image](https://github.com/user-attachments/assets/31a9eb42-ef00-41f3-8597-f03043e6c24f)


![image](https://github.com/user-attachments/assets/f2acb0f4-be0e-4f1e-968e-5164f33a7a94)

![image](https://github.com/user-attachments/assets/b74ab698-aaa3-4ab8-a447-2997ba0c7505)
