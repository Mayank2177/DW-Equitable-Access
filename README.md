# DW-Equitable-Access
This project aims to analyze data from the 78th Round of the Multiple Indicator Survey (MIS) to assess the percentage of the population with access to improved drinking water sources. The ultimate goal is to help ensure equitable access to clean water and contribute to India's progress on SDG targets.

# NOTE: you must set $API_KEY below using information retrieved from your IBM Cloud account 
(https://au-syd.dai.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html?context=cpdaas)

    export API_KEY=<your API key>


    export IAM_TOKEN=$(curl --insecure -X POST --location "https://iam.cloud.ibm.com/identity/token" \
    --header "Content-Type: application/x-www-form-urlencoded" \
    --header "Accept: application/json" \
    --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
    --data-urlencode "apikey=$API_KEY" | jq -r '.access_token')


# TODO:  manually define and pass values to be scored below

    curl --location "https://private.au-syd.ml.cloud.ibm.com/ml/v4/deployments/746a0994-f80f-4d03-a634-adc151ba4754/predictions?version=2021-05-01" \
    --header "Content-Type: application/json" \
    --header "Accept: application/json" \
    --header "Authorization: Bearer $IAM_TOKEN" \
    --data "{
        \"input_data\": [
            {
                \"fields\": [$ARRAY_OF_INPUT_FIELDS],
                \"values\": [[$ARRAY_OF_VALUES_TO_BE_SCORED], [$ANOTHER_ARRAY_OF_VALUES_TO_BE_SCORED]]
            }
        ]
    }"
