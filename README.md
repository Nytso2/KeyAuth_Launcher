# KeyAuth_Launcher

# KeyAuth C++ Integration Example

This is an example C++ project demonstrating how to integrate **KeyAuth** for user authentication. The program allows users to log in, register, upgrade, or activate using a license key. It utilizes KeyAuth's API for authentication and protects against unauthorized access using 2FA (Two-Factor Authentication).

## Features
- Login, registration, and license key activation.
- Subscription management and status tracking.
- 2FA support.
- Automatic creation of JSON files for auto-login credentials.

## Requirements
- C++ Compiler (e.g., Visual Studio, GCC)
- KeyAuth API Account (Obtain your API credentials from [KeyAuth](https://keyauth.cc/app/))
- Windows (for `Windows.h` usage)

## Setup

1. **Create a KeyAuth Application:**
   - Go to the [KeyAuth Dashboard](https://keyauth.cc/app/) and create an application to get the necessary credentials (name, ownerid, secret, etc.).

2. **Clone or Download the Repository:**
   - Clone or download this repository to your local machine.

3. **Configure the API Credentials:**
   - Replace the following variables in `keyauth_process.cpp` with your KeyAuth application credentials:
     ```cpp
     std::string name = skCrypt("").decrypt(); // App name
     std::string ownerid = skCrypt("").decrypt(); // Account ID
     std::string secret = skCrypt("").decrypt(); // Application secret
     std::string version = skCrypt("").decrypt(); // Application version
     std::string url = skCrypt("").decrypt(); // Custom domain or default KeyAuth URL
     std::string path = skCrypt("").decrypt(); // Optional, for tutorial references
     ```

4. **Build the Project:**
   - Compile the project using your preferred C++ IDE or compiler (e.g., Visual Studio).
   
5. **Run the Program:**
   - Run the `main.cpp` file. It will invoke the `Keyauth()` function, initiating the authentication process and providing options to the user (Login, Register, Upgrade, License Key).

## Usage

### KeyAuth Authentication Flow
When the program is run, the user will be presented with the following options:

- **[1] Login:** Enter username, password, and a 2FA code (if applicable).
- **[2] Register:** Create a new account with username, password, and a license key.
- **[3] Upgrade:** Upgrade an existing account using a license key.
- **[4] License Key Only:** Activate the application with a license key and 2FA (if enabled).

The program will handle successful logins and provide user data such as:
- Username
- IP Address
- Hardware ID
- Subscription details
- Account creation date and last login

The program will automatically create a JSON file for storing login credentials for future use (for example, for auto-login).

## 2FA (Two-Factor Authentication)

The program supports Two-Factor Authentication (2FA) for added security. You can enable or disable 2FA through the KeyAuth API. The application includes code to request the 2FA code during login or license activation if needed.

### Example Code Snippets:

**Login Example:**
```cpp
KeyAuthApp.login(username, password, TfaCode);
