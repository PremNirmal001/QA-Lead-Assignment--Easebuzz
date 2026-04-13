**1** GET /posts – validate status = 200. 



pm.response.to.have.status(200);



2 POST /posts – create a new post and verify the response contains the same title/body. (JSON)





Sample payload 



{

&#x20; "title": "foo",

&#x20; "body": "bar",

&#x20; "userId": 1

}





Validation



pm.response.to.have.status(201);

pm.expect(response.title).to.eql('foo');

pm.expect(response.body).to.eql('bar');





3 DELETE /posts/{id} – verify response status 200 or 204.



pm.expect(pm.response.code).to.be.oneOf(\[200, 204]);



Open Postman

Click Import

Upload the downloaded JSON file

Run collection using Collection Runner





I created a Postman collection with GET, POST, and DELETE APIs, added test scripts using pm.test, validated status codes, and verified response data using assertions.



