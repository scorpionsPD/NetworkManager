# NetworkManager

To use this code, you would first create a data model that conforms to the Decodable protocol, for example:

   struct User: Decodable {
   
     let id: Int
     let name: String
     let email: String
 }

Then, you would create an instance of NetworkManager and call the fetch method with the URL of the REST API endpoint:

 let networkManager = NetworkManager()

 let url = URL(string: "https://example.com/users")!
 

   networkManager.fetch(url: url) { (result: Result<[User]>) in
    
    switch result {
    case .success(let users):
       print(users)
    case .failure(let error):
       print(error)
     }
  }


In this example, the completion handler expects an array of User objects, so we specify Result<[User]> as the type parameter when calling the fetch method. The result object will either contain an array of User objects, or an error if something went wrong.
