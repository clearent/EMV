#EMV
<html>
<head>
<script type="text/javascript">
    window.addEventListener(
            "load",
            function(){
                processTextAreas();
            },
            false
    );

    function processTextAreas(){
        var div, ta = document.getElementsByTagName('textarea');
        // need to walk backwards because we are deleting nodes when done with them
        // and walking forward would screw up element indices
        for (var i = ta.length -1; i>=0;i--){
            console.log('--------------------------------');
            console.log(ta[i].innerHTML);
            div = document.createElement('div');
            ta[i].parentNode.insertBefore(div,ta[i]);
            div.innerHTML = '<pre>' + ta[i].innerHTML + '</pre>';
            ta[i].parentNode.removeChild(ta[i]);
        }
    }

</script>
</head>
<body>
<div class="container">
    <h3> Transaction </h3>

    <p> All fields are in alpha-numeric format</p>

    <table class="api">
        <tr>
            <td><strong>Field Name</strong></td>
            <td><strong>Notes</strong></td>
        </tr>
        <tr>
            <td><strong>amount</strong></td>
            <td>Amount of the Transactions.</td>
        </tr>
        <tr>
            <td><strong>authorization-code</strong></td>
            <td>Authorization code from issuer.</td>
        </tr>
        <tr>
            <td><strong>avs-result-code</strong></td>
            <td>Status of AVS check with the issuer.</td>
        </tr>
        <tr>
            <td><strong>avs-street</strong></td>
            <td>Status of AVS check with the issuer.</td>
        </tr>
        <tr>
            <td><strong>avs-zip</strong></td>
            <td>Status of AVS check with the issuer.</td>
        </tr>
        <tr>
            <td><strong>id</strong></td>
            <td>ID of the transaction. This can be used to do follow up transactions (i.e., void, refund, capture, etc.).</td>
        </tr>
        <tr>
            <td><strong>invoice </strong></td>
            <td>Invoice number if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>description</strong></td>
            <td>Description if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>comments</strong></td>
            <td>Comments if they were provided in the request.</td>
        </tr>
        <tr>
            <td><strong>original-amount</strong></td>
            <td>Original Amount of the transaction.</td>
        </tr>
        <tr>
            <td><strong>tip-amount</strong></td>
            <td>Tip amount if one was provided. If tip is adjusted this will be the adjusted tip amount.</td>
        </tr>
        <tr>
            <td><strong>tip-adjusted-amount</strong></td>
            <td>The difference between the new tip amount and original tip amount. Only present on an adjusted tip.</td>
        </tr>
        <tr>
            <td><strong>server-id</strong></td>
            <td>Server ID if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>created</strong></td>
            <td>Date transaction was run.</td>
        </tr>
        <tr>
            <td><strong>ref-id</strong></td>
            <td>ID of transactions that is tied to current transaction. For example, for a capture transaction the auth’s transaction id will be populated in the ref-id.</td>
        </tr>
        <tr>
            <td><strong>entry-method</strong></td>
            <td>How the data was entered, keyed or swiped.</td>
        </tr>
        <tr>
            <td><strong>first-recurring-transaction</strong></td>
            <td>Indicator if transaction was the first transaction to initiate recurring payments.</td>
        </tr>
        <tr>
            <td><strong>batch-string-id</strong></td>
            <td>The number of the batch that this transaction was included in.</td>
        </tr>
        <tr>
            <td><strong>type</strong></td>
            <td>Type of transaction (i.e., void, capture, auth, refund).</td>
        </tr>
        <tr>
            <td><strong>order-id</strong></td>
            <td>Order Id if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>purchase-order</strong></td>
            <td>Purchase order number if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>customer-id</strong></td>
            <td>Customer Id if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>email-address</strong></td>
            <td>Email address if one was provided in the request.</td>
        </tr>
        <tr>
            <td><strong>result</strong></td>
            <td>Result of the transaction. APPROVED, DECLINED, etc.</td>
        </tr>
        <tr>
            <td><strong>display-message</strong></td>
            <td>Display friendly result of the transaction.</td>
        </tr>
        <tr>
            <td><strong>result-code</strong></td>
            <td>Numeric response message</td>
        </tr>
        <tr>
            <td><strong>billing-is-shipping</strong></td>
            <td>True if billing address and shipping address are the same.</td>
        </tr>
        <tr>
            <td><strong>shipping</strong></td>
            <td>Address Object represents the shipping address. Not returned if no shipping address was provided or if the billing-is-shipping is set to true.</td>
        </tr>
        <tr>
            <td><strong>billing</strong></td>
            <td>Address Object represents the billing address. Not returned if no address was provided.</td>
        </tr>
        <tr>
            <td><strong>card</strong></td>
            <td>Last 4 digits of the card number.</td>
        </tr>
        <tr>
            <td><strong>tip-adjusted</strong></td>
            <td>True if tip was adjusted from original amount.</td>
        </tr>
        <tr>
            <td><strong>exp-date</strong></td>
            <td>Expiration date of the card.</td>
        </tr>
        <tr>
            <td><strong>csc</strong></td>
            <td>CSC of the card, Not returned if no csc was provided.</td>
        </tr>
        <tr>
            <td><strong>csc-result-code</strong></td>
            <td>Not returned if no CSC was provided.</td>
        </tr>
        <tr>
            <td><strong>client-ip</strong></td>
            <td>Ip of originated transaction. Not returned if not provided.</td>
        </tr>
        <tr>
            <td><strong>emv-data</strong></td>
            <td>Request EMV tags in tag-length-value format (a.k.a. TLV)

                EMV entry methods:
                <ul>EMV_DIP</ul>
                <ul>EMV_CONTACTLESS</ul>
                <ul>EMV_FALLBACK_SWIPE</ul>
                </li>
            </td>
        </tr>
        <tr>
            <td><strong>csm</strong></td>
            <td>Cardholder Verification Method (only for EMV transactions):


                <ul>NON (no cardholder verification method)</ul>
                <ul>MSG (Manual verification of signature)</ul>
                <ul>OFC (Offline PIN in clear)</ul>
                </li>
            </td>
        </tr>

        <tr>
            <td><strong>key-serial-number</strong></td>
            <td>Device serial number used to encrypt emv data
            </td>
        </tr>
    </table>


    <h3> EMV Contact Sale </h3>

    <p>Contact EMV transactions are only supported through the RESTful API. The Request must include the track data, the EMV data elements in TLV format, the entry method “EMV_DIP” for contact transactions and the key serial number provide by
        the device. CVM element is optional XML Request </p>

    <table class="api" class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    <transaction>
        <type>SALE</type>
        <amount>11.11</amount>
        <track-format>Track2</track-format>
        <track2-data> … Track2 …</track2-data>
        <emv-data> 4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
        <emv-entry-method>EMV_DIP</emv_entry-method>
            <key-serial-number> ……………</key-serial-number>
            <cvm>MSG</cvm>
    </textarea>
            </td>
            <td>
    <textarea>
    <response>
        <code>200</code>
        <status>success</status>
        <exchange-id>ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2542</exchange-id>
        <links>
            <rel>transaction</rel>
            <href>/rest/v2/transactions?id=111057</href>
            <id>111057</id>
        </links>
        <payload type="transaction">
            <transaction>
                <amount>11.11</amount>
                <authorization-code>TAS289</authorization-code>
                <id>111057</id>
                <type>SALE</type>
                <result>Approved</result>
                <display-message>Transaction approved</display-message>
                <result-code>0000</result-code>
                <emv-data> F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
                <key-serial-number>………………..</key-serial-number>
            </transaction>
        </payload>
    </response>
    </textarea>
            </td>
        </tr>
        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    {

       "type":"SALE",
       "amount":"11.11",
       "track-format":"Track2",
       "track2-data":"---track2---",
       "emv-data":"4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131",
       "emv-entry-method":"EMV_DIP",
       "key-serial-number":"-----------",
       "cvm":"MSG",

    }
    </textarea>
            </td>
            <td>
    <textarea>
    <response>
        <code>200</code>
        <status>success</status>
        <exchange-id>ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2542</exchange-id>
        <links>
            <rel>transaction</rel>
            <href>/rest/v2/transactions?id=111057</href>
            <id>111057</id>
        </links>
        <payload type="transaction">
            <transaction>
                <amount>11.11</amount>
                <authorization-code>TAS289</authorization-code>
                <id>111057</id>
                <type>SALE</type>
                <result>Approved</result>
                <display-message>Transaction approved</display-message>
                <result-code>0000</result-code>
                <emv-data> F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
                <key-serial-number>………………..</key-serial-number>
            </transaction>
        </payload>
    </response>
    </textarea>
            </td>
        </tr>
    </table>


    <h3>EMV Contactless Sale </h3>

    <p>Contactless EMV transactions are only supported through the RESTful API. The Request must include the track data, the EMV data elements in TLV format, the entry method “EMV_CONTACTLESS” for contact transactions and the key serial number
        provide by the device. CVM element is optional </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    <transaction>
        <type>SALE</type>
        <amount>11.11</amount>
        <track-format>Track2</track-format>
        <track2-data> … Track2 …</track2-data>
        <emv-data> 4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
        <emv-entry-method>EMV_CONTACTLESS</emv_entry-method>
            <key-serial-number> ……………</key-serial-number>
            <cvm>MSG</cvm>
            <is-contactless>true</is-contactless>

    </textarea>
            </td>
            <td>
    <textarea>

    {
      "code": "200",
      "status": "success",
      "exchange-id": "ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2549",
      "payload": {
        "transaction": {
          "amount": "11.11",
          "id": "111058",
          "invoice": "457",
           "type": "SALE",
          "result": "Approved",
          "authorization-code": "TAS371",
          "avs-result-code": "N",
          "batch-string-id": "297",
          "display-message": "Transaction approved",
          "result-code": "0000",
          "billing-is-shipping": "false",
        },
        "payloadType": "transaction"
      },
      "links": [
        {
          "rel": "transaction",
          "href": "/rest/v2/transactions?id=111058",
          "id": "111058"
        }
      ]
    }

    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    {

       "type":"SALE",
       "amount":"11.11",
       "track-format":"Track2",
       "track2-data":"---track2---",
       "emv-data":"4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131",
       "emv-entry-method":"EMV_CONTACTLESS",
       "key-serial-number":"-----------",
       "cvm":"MSG",
        "is-contactless":"true"
    }
    </textarea>
            </td>
            <td>
    <textarea>

    {
      "code": "200",
      "status": "success",
      "exchange-id": "ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2549",
      "payload": {
        "transaction": {
          "amount": "11.11",
          "id": "111058",
          "invoice": "457",
           "type": "SALE",
          "result": "Approved",
          "authorization-code": "TAS371",
          "avs-result-code": "N",
          "batch-string-id": "297",
          "display-message": "Transaction approved",
          "result-code": "0000",
          "billing-is-shipping": "false",
        },
        "payloadType": "transaction"
      },
      "links": [
        {
          "rel": "transaction",
          "href": "/rest/v2/transactions?id=111058",
          "id": "111058"
        }
      ]
    }
    </textarea>
            </td>
        </tr>
    </table>


    <h3>Fall Back EMV transaction </h3>

    <p>Fallback EMV transactions are only supported through the RESTful API. The Request must include the track data and the entry method “EMV_FALLBACK_SWIPE” for fallback transactions. CVM element is optional.

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    <transaction>
        <type>SALE</type>
        <amount>11.11</amount>
        <track-format>Track2</track-format>
        <track2-data> … Track2 …</track2-data>
        <emv-data> 4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
        <emv-entry-method> EMV_FALLBACK_SWIPE</emv_entry-method>
            <key-serial-number> ……………</key-serial-number>
            <cvm>MSG</cvm>


    </textarea>
            </td>
            <td>
    <textarea>
        <response>
            <code>200</code>
            <status>success</status>
            <exchange-id>ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2542</exchange-id>
            <links>
                <rel>transaction</rel>
                <href>/rest/v2/transactions?id=111057</href>
                <id>111057</id>
            </links>
            <payload type="transaction">
                <transaction>
                    <amount>11.11</amount>
                    <authorization-code>TAS289</authorization-code>
                    <id>111057</id>
                    <type>SALE</type>
                    <result>Approved</result>
                    <display-message>Transaction approved</display-message>
                    <result-code>0000</result-code>
                    <emv-data> F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
                    <key-serial-number>………………..</key-serial-number>
                </transaction>
            </payload>
        </response>


    </textarea>
            </td>

        <tr>
            <td>JSON Request</td>
            <td>JSON Response</td>
        <tr>
            <td>
    <textarea>
    {

       "type":"SALE",
       "amount":"11.11",
       "track-format":"Track2",
       "track2-data":"---track2---",
       "emv-data":"4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131",
       "emv-entry-method":" EMV_FALLBACK_SWIPE",
       "key-serial-number":"-----------",
       "cvm":"MSG"

    }
    </textarea>
            </td>
            <td>
    <textarea>

    {
      "code": "200",
      "status": "success",
      "exchange-id": "ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2549",
      "payload": {
        "transaction": {
          "amount": "11.11",
          "id": "111058",
          "invoice": "457",
           "type": "SALE",
          "result": "Approved",
          "authorization-code": "TAS371",
          "avs-result-code": "N",
          "batch-string-id": "297",
          "display-message": "Transaction approved",
          "result-code": "0000",
          "billing-is-shipping": "false",
        },
        "payloadType": "transaction"
      },
      "links": [
        {
          "rel": "transaction",
          "href": "/rest/v2/transactions?id=111058",
          "id": "111058"
        }
      ]
    }
    </textarea>
            </td>
    </table>


    <h3>EMV with tips </h3>

    <p>For EMV Tips you will follow the same process we are using today. You will do an auth with the card data and in this case the EMV information. Then a capture with the tip amount.

    </p>

    <table class="api">
        <tr>
            <td>XML Request</td>
            <td>XML Response</td>
        <tr>
            <td>
    <textarea>
    <transaction>
        <type>AUTH</type>
        <amount>11.11</amount>
        <track-format>Track2</track-format>
        <track2-data> … Track2 …</track2-data>
        <emv-data> 4F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
        <emv-entry-method> EMV_DIP</emv_entry-method>
            <key-serial-number> ……………</key-serial-number>
            <cvm>NON</cvm>


    </textarea>
            </td>
            <td>
    <textarea>
        <response>
            <code>200</code>
            <status>success</status>
            <exchange-id>ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2542</exchange-id>
            <links>
                <rel>transaction</rel>
                <href>/rest/v2/transactions?id=111057</href>
                <id>111057</id>
            </links>
            <payload type="transaction">
                <transaction>
                    <amount>11.11</amount>
                    <authorization-code>TAS289</authorization-code>
                    <id>111057</id>
                    <type>SALE</type>
                    <result>Approved</result>
                    <display-message>Transaction approved</display-message>
                    <result-code>0000</result-code>
                    <emv-data> F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
                    <key-serial-number>………………..</key-serial-number>
                </transaction>
            </payload>
        </response>



    </textarea>
            </td>
        <tr>
            <td>Capture Request XML</td>
            <td>Capture Response XML</td>
        </tr>
        <tr>
            <td>
    <textarea>
    <transaction>
        <type>Capture</type>
        <amount>25.00</amount>
        <tip-amount>4.00</tip-amount>
        <id>111057</id>
    </transaction>
    </textarea>
            </td>
            <td>
    <textarea>

        <response>
            <code>200</code>
            <status>success</status>
            <exchange-id>ID-CLADEVDOCKER-smx01-39717-1418080195075-1-2542</exchange-id>
            <links>
                <rel>transaction</rel>
                <href>/rest/v2/transactions?id=111057</href>
                <id>111057</id>
            </links>
            <payload type="transaction">
                <transaction>
                    <amount>11.11</amount>
                    <authorization-code>TAS289</authorization-code>
                    <id>111057</id>
                    <type>SALE</type>
                    <result>Approved</result>
                    <display-message>Transaction approved</display-message>
                    <result-code>0000</result-code>
                    <emv-data> F07A00000000310109F120F4352454449544F2044452056495341500B56495341204352454449545F300202015F3401015F2503090701C20131</emv-data>
                    <key-serial-number>………………..</key-serial-number>
                </transaction>
            </payload>
        </response>
    </textarea>
            </td>
        </tr>

    </table>
</div>
</body>
</html>
