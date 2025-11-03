## I. System Overview

This document arranges the system's core functions, topology structure, and detailed operational procedures, covering modules such as device control, task management, media management, and account permissions.

## II. Core Functional Modules

### 1. Equipment Control and interaction

As indicated in files such as `CONN commands-EN.md` and `Other Commands.md`, the system supports direct control of devices (such as control cards), with primary functions including:

- **Screenshot Operations**： Supports two screenshot methods (Android full-screen capture `ScreenshotBySize`, camera capture `GetScreenshotByCamera`). Commands can be sent to the server via the web interface; upon execution, the device returns screenshot data (base64 string or null value).
- **Screen Management**
  - Manual Screen Control: Directly manage device screen status via the `SwitchScreen` command (`turnOn: true/false`).
  - Scheduled Screen Tasks: Create/modify timed tasks using `TaskKeepingScreenOn` (supporting time range and periodic filtering), with task details retrievable via `GetTaskToKeepScreenOn`.
- **Volume Control**: Supports manual volume adjustment (`set volume by manual`) and creation of scheduled volume tasks (`TaskSettingVolume`), including task scheduling parameters.
- **Additional Controls**: Set device background, switch server connections, toggle log reporting.

### 2.Task and Advertisement Management

Based on files such as `Task_ad-EN.md` and `group ads-EN.md`, the system supports the management of advertising tasks:

- Advertising Task Operations
  -  Create / Manage advertising tasks (supporting scheduled deployment and offline deployment).
  -  Query task details: Retrieve deployed device lists (Excel format) via `getPlaceDetail`, and offline device lists via `getOfflineDetail`.
  - Data statistics: Download ad reception reports (`downloadReceivePlaceGroupAdReport`) and offline command reception reports (`downloadReceiveOfflineAdReport`).
- **Task Status Management**: Task statuses include `Created`, `StartPlace`, `PlaceFinished`, etc. Only specific statuses (e.g., `StartPlace`) permit querying placement details.

### 3. Media File Management

Media Files-EN.md details the upload, download, and query functions for media files:

- File Operations
  - Upload media files (images, audio, video, etc., `/v1/cms/media/upload`), device parameter files (`/v1/cms/media/uploadCscFile`).
  - Download media files (download after querying via `/v1/cms/media/list`), device parameter files (`/v1/cms/media/downloadCscFile`).
  - Query file list: Supports filtering by type (`media_type`) and pagination, returning file ID, size, MD5 checksum, and other details.

### 4. Account and Permissions Management

`Account API.md`、`Users modem-EN.md`、`User group modem-EN.md`Concerning account and access control：

- Account Operations
  - Corporate Accounts: Upload business licence and platform verification documents (`/v1/cms/account/uploadCompanyLicense`), download verification documents (`/v1/cms/account/:id/downAuthConfirmation`).
  - Personal Accounts: Upload front and back sides of ID card (`/v1/cms/account/uploadPersonalLicence`).
  - Download platform confirmation file sample (`/v1/cms/account/downloadConfirmationFile`).。
- Permission Control
  - User/user group permissions encompass granular control over device functions (e.g., screen toggle, screenshot capture), task management (e.g., creating advertising tasks), and media handling (e.g., file uploads) via specific permissions (e.g., `set screen switch by manual`, `upload media file`).
  - Administrators may query detailed user/user group permissions to regulate functional access scopes.

### 6. API Calls and Debugging

`Vehicle HUB Platform API Call Manual.md` provides a practical guide for API calls:

- **Call Process**: Using the passenger flow statistics interface as an example, employ the Postman tool to complete the path, request method, and parameters according to the API documentation, then send the request with the token (`auth_token`).
- **FAQ**: Should a path be unavailable, consult the platform console; utilise platform query commands to retrieve request paths and methods.

## III. System Topology Diagram

```plaintext
┌─────────────┐          ┌─────────────┐          ┌─────────────┐
│ Web Frontend│          │   Server    │          │   Device    │
│（Send Command)│ API Request   │（Forward Command)│ Forward Command│ （Execute Command）  │
│ e.g:Switch Screen  │─────────>│ e.g:Switch Screen │─────────>│  e.g:Switch Screen   │
└─────────────┘          └─────────────┘          └─────────────┘
        ▲                        ▲                        │
        │                        │                        │
        │                        │                        │
        │       Results returned        │ Result transmission        │
        └────────────────────────┼────────────────────────┘
                                 │
                                 ▼
                     （Returned results: e.g. screenshots, status）
```

- **Description** ：The web frontend sends commands to the server via API (e.g., screen on/off, file upload), which the server forwards to the device for execution. The device then transmits the results (e.g., screenshots, status) back through the server to the web frontend.

## IV. Detailed Operational Procedure

### 1. Device online procedure

1.  Log in to the platform and click `Download vehicle access certificate` in the top-right corner to download the access certificate (refer to `Vehicle HUB Platform API Calling Manual.md`).
2. Open the `ledok` tool, select the target control card, and import the certificate to complete configuration.
3. After the device comes online, verify the connection status via the platform console.

### 2. Switching Screen Operation Procedure

Interface Address: https://www.vehhub.vip/cms/v1/cms/conn/sendCommand/

#### （1）Manual Switch Screen

1. Web-based Construction

   ```
   SwitchScreen
   ```

   Command (example)：

   json

   ```json
   {
       "cardId": "e16-b19-40470",
       "turnOn": true,  // true For the opening screen，false It is a closed screen
       "_type": "SwitchScreen"
   }
   ```

   

2.  Sent to the server, which forwards it to the target device.

3.  The device executes the command and returns a status response.

#### （2）Creating a Scheduled Screen Switch Task

1. Sent via the web interface

   ```
   TaskKeepingScreenOn
   ```

   Command, comprising task ID, device ID, and scheduling parameters (such as time range, frequency）：

   json

   ```json
   {
       "taskId": "5e8d720fe3fd984c2ceb0770",
       "cardId": "e16-b19-40470",
       "_type": "TaskKeepingScreenOn"
   }
   ```

2. The server stores tasks and issues them to devices.

3.  Through

   ```
   GetTaskToKeepScreenOn
   ```

   Command to query task details：

   json

   ```json
   {
       "cardId": "e16-b19-40470",
       "_type": "GetTaskToKeepScreenOn"
   }
   ```

## 五、FAQ

1. **API path not found**: Look up the path via the platform console (refer to `Vehicle HUB Platform API Invocation Manual.md`).
2. **Without Sufficient Permissions**: Contact your administrator to enable the relevant permissions within User Groups / User Permissions (e.g., `set screen switch by manual`).
3. **File Upload Failure**: Verify the file type meets requirements (refer to the `media_type` definition in `Media Files-EN.md`) and ensure the token is valid.