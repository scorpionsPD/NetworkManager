# NetworkManager

To use this code, you would first create a data model that conforms to the Decodable protocol, for example:

   struct User: Decodable {
   
     let id: Int
     let name: String
     let email: String
 }

Then, you would create an instance of NetworkManager and call the fetch method with the URL of the REST API endpoint:

import NetworkLibrary

NetworkManager.shared.request(urlString: "https://api.example.com/data") { (result: Result<MyModel, NetworkError>) in
    switch result {
    case .success(let data):
        // Handle the successful response
        print(data)
    case .failure(let error):
        // Handle the error
        print(error)
    }
}


In this example, the completion handler expects an array of User objects, so we specify Result<MyModel> as the type parameter when calling the fetch method. The result object will either contain an array of User objects, or an error if something went wrong.
