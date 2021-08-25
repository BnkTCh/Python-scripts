import requests
from shareplum import Office365

# get data from configuration
username = '......'
password =	'......'
site_name = '......'
base_path = 'https://....'
doc_library = 'data'

file_name = "new.txt"

# Obtain auth cookie
authcookie = Office365(base_path, username=username, password=password).GetCookies()
session = requests.Session()
session.cookies = authcookie
session.headers.update({'user-agent': 'python_bite/v1'})
session.headers.update({'accept': 'application/json;odata=verbose'})


# perform the actual upload
with open(file_name, 'rb') as file_input:
    try:
        response = session.post(
            url=base_path + "/sites/" + site_name +
            "/_api/web/GetFolderByServerRelativeUrl('Shared%20Documents/" +
            doc_library+"')/Files/add(url='"
            + file_name + "',overwrite=true)",
            data=file_input)
    except Exception as err:
        print("Some error occurred: " + str(err))
