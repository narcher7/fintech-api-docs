# fintech-api-docs

When creating this test user guide, I used the following procedure:

1. I implemented a directory structure which would allow for the addition of future API pages. This includes adding metadata such as `nav_order` to the top of the page.
2. Based on the data in the API spec, I wrote an initial intro.
3. I reformatted and saved the provided spec as a `.yaml` file and created a collection in Postman for testing.
4. I used the Postman to generate a request example. Since I lacked authorization to the server's provided, I mocked the example responses based on the information provided in the API spec.
5. For the best practices section, I did some light research using Google, Stripe's documentation (for comparison), and GenAI tools to come up with a few suggestions relevant to a FinTech system administrator.
6. Lastly, I performed a final editorial pass.

Had this not been a solo exercise, I would've taken the following additional steps before pushing the user guide to production:

1. Have the product/engineering teams review the document to ensure technical accuracy.
2. Have a proper test environment so I don't have to mock up an example response.
3. Find additional opportunities within the document to link to existing documentation.


