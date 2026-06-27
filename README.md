🦀 Rust API Calls

A Rust project demonstrating how to make asynchronous API requests, fetch JSON data from external services, and deserialize responses into strongly typed Rust structures.

This project uses the GitHub API to retrieve repository stargazer information and explores practical concepts used in modern backend development.

⸻

✨ Features

* Send asynchronous HTTP GET requests
* Consume REST APIs
* Fetch data from the GitHub API
* Deserialize JSON into Rust structs
* Handle response data safely
* Async execution using Tokio
* Error handling with Rust

⸻

🚀 Project Overview

This application sends a request to the GitHub API and retrieves repository stargazer data.

Workflow:

Application
      ↓
Send API Request
      ↓
GitHub REST API
      ↓
Receive JSON Response
      ↓
Deserialize JSON
      ↓
Display User Information

⸻

🛠 Tech Stack

* Rust 🦀
* Tokio
* Reqwest
* Serde
* GitHub REST API

⸻

📦 Dependencies

[dependencies]
tokio = { version = "1", features = ["full"] }
reqwest = { version = "0.12", features = ["json"] }
serde = { version = "1", features = ["derive"] }

⸻

💻 Example Code

use serde::Deserialize;
use reqwest::{Client, Error};
use reqwest::header::USER_AGENT;
#[derive(Deserialize, Debug)]
struct User {
    login: String,
    id: u32,
}
#[tokio::main]
async fn main() -> Result<(), Error> {
    let request_url = format!(
        "https://api.github.com/repos/{owner}/{repo}/stargazers",
        owner = "rust-lang-nursery",
        repo = "rust-cookbook"
    );
    let client = Client::new();
    let response = client
        .get(&request_url)
        .header(USER_AGENT, "rust-api-client")
        .send()
        .await?;
    let users: Vec<User> = response.json().await?;
    for user in users {
        println!("User: {}", user.login);
        println!("ID: {}", user.id);
    }
    Ok(())
}

⸻

▶ Getting Started

Clone the repository:

git clone https://github.com/Hellboy28D/Rust-API-Calls.git

Move into project directory:

cd Rust-API-Calls

Run the application:

cargo run

⸻

📂 Project Structure

Rust-API-Calls
│
├── src
│   └── main.rs
│
├── Cargo.toml
├── Cargo.lock
├── README.md
└── .gitignore

⸻

🎯 Learning Goals

This project helped explore:

✅ Async programming with Tokio
✅ Making API calls with Reqwest
✅ Working with REST APIs
✅ JSON deserialization with Serde
✅ Struct modeling in Rust
✅ External crate integration

⸻

🚀 Future Improvements

* Add support for POST requests
* Handle pagination from GitHub API
* Add command-line arguments
* Improve error handling
* Support multiple APIs
* Display formatted output

⸻

Built with 🦀 + APIs + curiosity
