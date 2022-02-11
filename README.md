composer require mailjet/mailjet-apiv3-php
<?php
  require 'vendor/autoload.php';
  use \Mailjet\Resources;
  $mj = new \Mailjet\Client('ef4ef94297c5a91b56d4223438537358','e655d80a30531ba3f0439b4f0c680b38',true,['version' => 'v3.1']);
  $body = [
    'Messages' => [
      [
        'From' => [
          'Email' => "romainmalaterre@ecolediagonale.com",
          'Name' => "Romain"
        ],
        'To' => [
          [
            'Email' => "romainmalaterre@ecolediagonale.com",
            'Name' => "Romain"
          ]
        ],
        'Subject' => "Greetings from Mailjet.",
        'TextPart' => "My first Mailjet email",
        'HTMLPart' => "<h3>Dear passenger 1, welcome to <a href='https://www.mailjet.com/'>Mailjet</a>!</h3><br />May the delivery force be with you!",
        'CustomID' => "AppGettingStartedTest"
      ]
    ]
  ];
  $response = $mj->post(Resources::$Email, ['body' => $body]);
  $response->success() && var_dump($response->getData());
?>
