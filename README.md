# Payamak-panel PHP

## Introduction
Here we've provided a complete 3rd-party library (SDK) for PHP developers that covers both **SOAP** and **REST** webservices. Before using, make sure you have provided a [valid account in Pars corporation](https://pars.ws/).


## Installation
You can run the following **composer** command to have it:

```
composer require payamak-panel/php:1.0.0
```

## Usage
This is the simple usage for both REST and SOAP APIs:
```php

$restClient = new Rest_Client('username', 'password');
print_r($restClient->SendSMS('09123456789', '5000xxx', 'test sms', false));

$soapClient = new Soap_Client('username', 'password');
print_r($soapClient->SendSimpleSMS2('09123456789', '5000xxx', 'test sms', false));

```
Further demonstrations can be found inside the _rest-sample.php_ and _soap-sample.php_ files.

## REST or SOAP?
We support a small number of methods in REST against the SOAP web service that supports the entire ones.

## REST Methods
We're currently supporting the following methods in REST web service:

```php
$restClient->SendSMS($to, $from, $text, $isFlash);
$restClient->GetDeliveries2($recId);
$restClient->GetMessages($location, $from, $index, $count);
$restClient->GetCredit();
$restClient->GetBasePrice();
$restClient->GetUserNumbers();
$restClient->BaseServiceNumber($text, $to, $bodyId);
```

## SOAP Methods
We support a wide range of methods in SOAP web service. They're scope separated. Let's review all the SOAP web service methods.

### Send Web Service

```php
$soapClient->GetCredit();
$soapClient->GetDeliveries($recIds);
$soapClient->GetDeliveries3($recId);
$soapClient->GetSmsPrice($irancellCount, $mtnCount, $from, $text);
$soapClient->SendByBaseNumber($text, $to, $bodyId);
$soapClient->SendByBaseNumber2($text, $to, $bodyId);
$soapClient->SendByBaseNumber3($text, $to);
$soapClient->SendSimpleSMS($to, $from, $text, $isflash);
$soapClient->SendSimpleSMS2($to, $from, $text, $isflash);
$soapClient->SendSms($to, $from, $text, $isflash, $udh, $recId);
$soapClient->SendSms2($to, $from, $text, $isflash, $udh, $recId, $status, $filterId);
$soapClient->SendMultipleSMS($to, $from, $text, $isflash, $udh, $recId);
$soapClient->SendMultipleSMS2($to, $from, $text, $isflash, $udh, $recId);
```

### Receive Web Service

```php
$soapClient->ChangeMessageIsRead($msgIds);
$soapClient->GetInboxCount();
$soapClient->GetLatestReceiveMsg($sender, $receiver);
$soapClient->GetMessages($location, $from, $index, $count);
$soapClient->GetMessagesAfterID($location, $from, $count, $msgId);
$soapClient->GetMessagesFilterByDate($location, $from, $index, $count, $dateFrom, $dateTo, $isRead);
$soapClient->GetMessagesReceptions($msgId, $fromRows);
$soapClient->GetMessagesWithChangeIsRead($location, $from, $index, $count, $isRead, $changeIsRead);
$soapClient->GetOutBoxCount();
$soapClient->RemoveMessages($location, $msgIds);
```

### User Web Service

```php
$soapClient->AddUser($productId, $descriptions, $mobileNumber, $emailAddress, $nationalCode, 
        $name, $family, $corporation, $phone, $fax, $address, $postalCode, $certificateNumber);
$soapClient->AddUserWithLocation($productId, $descriptions, $mobileNumber, $emailAddress, $nationalCode, 
    $name, $family, $corporation, $phone, $fax, $address, $postalCode, $certificateNumber, $country, $province, $city);
$soapClient->AddUserWithMobileNumber($productId, $mobileNumber, $firstName, $lastName, $email);
$soapClient->AddUserWithMobileNumber2($productId, $mobileNumber, $firstName, $lastName, $userName, $email);
$soapClient->AddUserWithUserNameAndPass($productId, $descriptions, $mobileNumber, $emailAddress, $nationalCode, 
    $name, $family, $corporation, $phone, $fax, $address, $postalCode, $certificateNumber, $targetUserName, $targetUserPassword);
$soapClient->AuthenticateUser();
$soapClient->ChangeUserCredit($amount, $description, $targetUsername, $GetTax);
$soapClient->DeductUserCredit($amount, $description);
$soapClient->ForgotPassword($mobileNumber, $emailAddress, $targetUsername);
$soapClient->GetCities($provinceId);
$soapClient->GetEnExpireDate();
$soapClient->GetExpireDate();
$soapClient->GetProvinces();
$soapClient->GetUserBasePrice($targetUsername);
$soapClient->GetUserCredit($targetUsername);
$soapClient->GetUserCredit2();
$soapClient->GetUserDetails($targetUsername);
$soapClient->GetUserIsExist($targetUsername);
$soapClient->GetUserNumbers();
$soapClient->GetUserTransactions($targetUsername, $creditType, $dateFrom, $dateTo, $keyword);
$soapClient->GetUserWallet();
$soapClient->GetUserWalletTransaction($dateFrom, $dateTo, $count, $startIndex, $payType, $payLoc);
$soapClient->GetUsers();
$soapClient->RemoveUser($targetUsername);
```

### Voice Web Service

```php
$soapClient->SendBulkSpeechText($title, $body, $receivers, $DateToSend, $repeatCount);
$soapClient->SendBulkVoiceSMS($title, $voiceFileId, $receivers, $DateToSend, $repeatCount);
$soapClient->UploadVoiceFile($title, $base64StringFile);
```

### Contacts Web Service

```php
$soapClient->AddContact($groupIds, $firstname, $lastname, $nickname, $corporation, $mobilenumber,
        $phone, $fax, $birthdate, $email, $gender, $province, $city, $address, $postalCode, $additionaldate,
        $additionaltext, $descriptions);
$soapClient->AddContactEvents($contactId, $eventName, $eventType, $eventDate);
$soapClient->AddGroup($groupName, $Descriptions, $showToChilds);
$soapClient->ChangeContact($contactId, $firstname, $lastname, $nickname, $corporation, $mobilenumber,
        $phone, $fax, $email, $gender, $province, $city, $address, $postalCode, $contactStatus,
        $additionaltext, $descriptions);
$soapClient->ChangeGroup($groupId, $groupName, $Descriptions, $showToChilds, $groupStatus);
$soapClient->CheckMobileExistInContact($mobileNumber);
$soapClient->GetContactEvents($contactId);
$soapClient->GetContacts($groupId, $keyword, $from, $count);
$soapClient->GetContactsByID($contactId, $status);
$soapClient->GetGroups();
$soapClient->MergeGroups($originGroupId, $destinationGroupId, $deleteOriginGroup);
$soapClient->RemoveContact($mobilenumber);
$soapClient->RemoveContactByContactID($contactId);
$soapClient->RemoveGroup($groupId);
```

### Schedule Web Service

```php
$soapClient->AddNewMultipleSchedule($to, $from, $text, $isflash, $scheduleDateTime, $period);
$soapClient->AddNewUsance($to, $from, $text, $isflash, $scheduleStartDateTime, $countrepeat,
        $scheduleEndDateTime, $periodType);
$soapClient->AddSchedule($to, $from, $text, $isflash, $scheduleDateTime, $period);
$soapClient->GetScheduleDetails($scheduleId);
$soapClient->GetScheduleStatus($scheduleId);
$soapClient->RemoveSchedule($scheduleId);
```

### Bulk Web Service

```php
$soapClient->AddNumberBulk($from, $title, $messages, $receivers, $DateToSend);
$soapClient->BulkReception($bulkId, $maximumRows, $startRowIndex);
$soapClient->BulkReceptionCount($bulkId);
$soapClient->GetBulkDeliveries($recIds);
$soapClient->GetBulkDeliveries2($recId);
$soapClient->GetBulkDetails($bulkdId);
```
