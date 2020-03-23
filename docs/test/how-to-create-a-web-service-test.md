---
title: Vytvoření testu webové služby
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a6e42d6d92a74a0fc8be96c966b9146b7888b9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589094"
---
# <a name="how-to-create-a-web-service-test"></a>Postupy: Vytvoření testu webové služby

K testování webových služeb můžete použít test výkonu webu. Pomocí možností **Vložit požadavek a** Vložit **požadavek webové služby** můžete přizpůsobit jednotlivé požadavky v **Editoru testů výkonu webu** a vyhledat stránky webové služby. Obvykle se tyto stránky nezobrazují ve webové aplikaci. Pro přístup k těmto stránkám je tedy nutné přizpůsobit požadavek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postupy používají webovou službu, která je obsažena v commerce starter kit. Můžete si jej stáhnout z [ASP.NET commerce starter kit](https://sourceforge.net/projects/ppcsk/).

**Požadavky**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Testování webové služby

1. Vytvořte nový test výkonu webu. Jakmile se prohlížeč otevře, zvolte **Zastavit**.

2. V **Editoru webových testů výkonu**klepněte pravým tlačítkem myši na test výkonu webu a vyberte příkaz **Přidat požadavek webové služby**.

3. Do vlastnosti **Url** nového požadavku zadejte název webové **http://localhost/storecsvs/InstantOrder.asmx**služby, například .

4. Otevřete samostatnou relaci prohlížeče a na panelu nástrojů **Adresa** zadejte adresu URL stránky *ASMX.* Zvolte metodu, která má být testována, a prohlédněte si zprávu protokolu SOAP. Obsahuje hlavičku `SOAPAction`.

5. V **Editoru testů výkonnosti webu**klikněte pravým tlačítkem myši na požadavek a **výběrem možnosti Přidat záhlaví** přidejte nové záhlaví. Do **Name** vlastnosti Name `SOAPAction`zadejte . Do vlastnosti **Value** zadejte hodnotu, která se zobrazí v `SOAPAction`, například `"http://tempuri.org/CheckStatus"`.

6. Rozbalte uzel URL v editoru, zvolte uzel **Text řetězce** a ve `text/xml`vlastnosti Typ **obsahu** zadejte hodnotu .

7. Vraťte se do prohlížeče v kroku 4, vyberte část XML požadavku SOAP ze stránky s popisem webové služby a zkopírujte ji do schránky.

8. Obsah kódu XML je podobný následujícímu příkladu:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Vraťte se do **editoru testů výkonu webu** a pak zvolte tři tečky **(...)** ve vlastnosti **Tělo řetězce.** Vložte obsah schránky do vlastnosti.

10. Aby test proběhl úspěšně, je zapotřebí všechny zástupné hodnoty v kódu XML nahradit platnými hodnotami. V předchozí ukázce by byly nahrazeny dvě instance typu `string` a jedna typu `int`. Tato operace webové služby bude dokončena pouze v případě, že je registrován uživatel, který zadal objednávku.

11. Klepněte pravým tlačítkem myši na požadavek webové služby a vyberte **přidat parametr querystring url**.

12. Parametru řetězce dotazu přiřaďte název a hodnotu. V předchozím příkladu je `op` název a `CheckStatus`hodnota je . To identifikuje operaci webové služby, která má být vyvedena.

    > [!NOTE]
    > Pomocí `{{DataSourceName.TableName.ColumnName}}` datové vazby v těle SOAP můžete nahradit libovolnou zástupnou hodnotu hodnotami vázanými na data pomocí syntaxe.

13. Spusťte test. V horním podokně **prohlížeče výsledků testů výkonnosti webu**vyberte požadavek webové služby. V dolním podokně vyberte kartu webový prohlížeč. Xml, který je vrácen webovou službou a výsledky všech operací, se zobrazí.

## <a name="see-also"></a>Viz také

- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
