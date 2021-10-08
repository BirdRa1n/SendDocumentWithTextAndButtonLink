# SendDocumentTelegramBot <h1>
* Envia Mensagem
* Documento
* Exibe um botão com hyperlink
~~~php
//$msg = strip_tags(nl2br($_POST['texto']));
        $title = $_POST['title'];
        $date = $_POST['delivery_date'];
        $materia = $_POST['materia'];
        $credts = $_POST['credts'];
        $link = $_POST['link'];
        $name_file = 'file.pdf';

        $msg = "Olá, Você está testando o meu código\nCréditos: TheDarioJr";

        $token = '<YourToken>';

        $ch = curl_init();
        curl_setopt($ch, CURLOPT_POST, true);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
        curl_setopt($ch, CURLOPT_HTTPHEADER, ['Content-Type: multipart/form-data']);
        curl_setopt($ch, CURLOPT_URL, "https://api.telegram.org/bot{$token}/sendDocument");
        curl_setopt($ch, CURLOPT_ENCODING, '');
        curl_setopt($ch, CURLOPT_MAXREDIRS, 10);
        curl_setopt($ch, CURLOPT_TIMEOUT, 0);
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
        curl_setopt($ch, CURLOPT_HTTP_VERSION, CURL_HTTP_VERSION_1_1);
        curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'POST');

        $postFields = array(
            'chat_id' => 'YourToken',
            'document' => 'https://url_file' . "$name_file",
            'caption' => $msg,
            'reply_markup' => '{"inline_keyboard":[[{"text":"Button Link","url":"' . $link . '"}]]}'
        );
        curl_setopt($ch, CURLOPT_POSTFIELDS, $postFields);
        if (!curl_exec($ch))
            echo curl_error($ch);
        curl_close($ch);
~~~
