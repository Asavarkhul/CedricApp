# CedricApp 

This is a simple SwiftUE application that fetches user data from the ([Random User API](https://randomuser.me/) and displays both the user's name and picture in a list. It uses `Swift Concurrency (async/await)`, also `@published` properties for reactivity, and a repository approach for network calls.

## Overview

**SwiftUI** for the UI layer  
* Asynchronous network calls using Swift Concurrency (async/await) 
** MVVM + Repository pattern:
  - **ViewModel**: [UserListViewModel]  
  - **Repository**: [UserListRepository] (fetches from the Random User API)  
  - **Models**: [UserListResponse] (for decoding API JSON) and [User] (domain model) 
* Macro-based Testing* for verifying both the ViewModel and Repository 

## Project Structure


```shell
MySimpleRandomUserApp/
 ┣ Models/
 ┃ ┣ UserListResponse.swift    (API response model: UserResponse, UserName, UserPicture)
 ┃ ┗ User.swift               (domain model)
 ┣ Repositories/
 ┃ ┗ UserListRepository.swift (handles network call, decodes JSON)
 ┣ ViewModels/
 ┃ ┗ UserListViewModel.swift  (fetches data, transforms to domain model, published states)
 ┣ Views/
 ┃ ┗ ContentView.swift        (UI: displays list of fetched users)
 ┣ Tests/
 ┃ ┣ UserListViewModelTests.swift
 ┃ ┗ UserListRepositoryTests.swift
 ┗ MySimpleRandomUserApp.swift (entry point)
```


## Requirements

- **application target**: Excode 15 (or later)
- **iOS 16+** (or iOS 17+) deployment target, depending on the SwiftUI/concurrency features you use

## Installation & Usage

1. **Clone the repository**;

```bash
git clone https://github.com/Asavarkhul/CedricApp.git
```

2. **Open the project** in Xcode:

```bash
cd CedricApp
open Cedric.xcodeproj
```

3. **Select a Simulator** or your connected device in the Xcode toolbar.
4. **Run** the app (CMD + R).

When the app launches, it will:

- Show a loading indicator briefly.
- Display a list of random users (their names and thumbnails) fetched from [randomuser.me](https://randomuser.me/).

## Testing

This project uses macro-based tests (import Testing, @Test, #expect) and Swift Concurrency testing. All test files are located in the Tests/ folder.


- **UserListViewModelTests.swift**
  Verifies that the ViewModel correctly fetches users (both success and failure paths) using a mock repository. Ensures that published properties like $users, $isLoading, $error update as expected.

- **UserListRepositoryTests.swift**
  Tests the (UserListRepository) by injecting a custom closure that simulates success (returning mock JSON) or failure (throwing an error). Checks the decoded JSON is correct and that errors are handled properly.


`bash
# How to Run Tests:

In XCode, press CMD + U

The test output (success/failure) appears in the Test Navigator.
```
---

