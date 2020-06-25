---
title: Vytvoření testu webové služby
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67aff3b1486224c93a6a8302feb96caea91afcff
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287893"
---
# <a name="how-to-create-a-web-service-test"></a>Postupy: Vytvoření testu webové služby

K testování webových služeb můžete použít test výkonnosti webu. Pomocí možností **Vložení požadavku** a **vložení žádosti o webovou službu** můžete přizpůsobit jednotlivé požadavky v **Editor testu výkonnosti webu** k vyhledání stránek webové služby. Obvykle tyto stránky ve webové aplikaci nezobrazujete. Pro přístup k těmto stránkám je tedy nutné přizpůsobit požadavek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postupy používají webovou službu, která je obsažena v sadě Commerce Starter Kit. Můžete si ho stáhnout z [ASP.NET Commerce Starter Kit](https://sourceforge.net/projects/ppcsk/).

**Požadavky**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Testování webové služby

1. Vytvořte nový test výkonnosti webu. Jakmile se prohlížeč otevře, klikněte na tlačítko **zastavit**.

2. V **Editor testu výkonnosti webu**klikněte pravým tlačítkem na test výkonnosti webu a vyberte **Přidat žádost o webovou službu**.

3. Do vlastnosti **Adresa URL** nového požadavku zadejte název webové služby, například **http://localhost/storecsvs/InstantOrder.asmx** .

4. Otevřete samostatnou relaci prohlížeče a na panelu nástrojů **adresa** zadejte adresu URL stránky *. asmx* . Zvolte metodu, která má být testována, a prohlédněte si zprávu protokolu SOAP. Obsahuje hlavičku `SOAPAction`.

5. V **Editor testu výkonnosti webu**klikněte pravým tlačítkem myši na požadavek a výběrem **Přidat hlavičku** přidejte novou hlavičku. Do vlastnosti **název** zadejte `SOAPAction` . Do vlastnosti **hodnota** zadejte hodnotu, která se zobrazí v `SOAPAction` , například `"http://tempuri.org/CheckStatus"` .

6. Rozbalte uzel adresa URL v editoru, vyberte uzel **tělo řetězce** a v vlastnosti **typ obsahu** zadejte hodnotu `text/xml` .

7. V kroku 4 se vraťte do prohlížeče, vyberte část XML požadavku SOAP ze stránky popis webové služby a zkopírujte ji do schránky.

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

9. Vraťte se do **Editor testu výkonnosti webu** a pak ve vlastnosti **tělo řetězce** zvolte tři tečky **(...)** . Vložte obsah schránky do vlastnosti.

10. Aby test proběhl úspěšně, je zapotřebí všechny zástupné hodnoty v kódu XML nahradit platnými hodnotami. V předchozí ukázce by byly nahrazeny dvě instance typu `string` a jedna typu `int`. Tato operace webové služby se dokončí jenom v případě, že existuje registrovaný uživatel, který si umístil objednávku.

11. Klikněte pravým tlačítkem na požadavek webové služby a vyberte **Přidat parametr QueryString adresy URL**.

12. Parametru řetězce dotazu přiřaďte název a hodnotu. V předchozím příkladu je název `op` a hodnota je `CheckStatus` . Tím se identifikuje operace webové služby, která se má provést.

    > [!NOTE]
    > Datovou vazbu v těle protokolu SOAP můžete použít k nahrazení libovolné zástupné hodnoty hodnotami vázanými daty pomocí `{{DataSourceName.TableName.ColumnName}}` syntaxe.

13. Spusťte test. V horním podokně **prohlížeče webového výkonu výsledky testů**vyberte požadavek webové služby. V dolním podokně vyberte kartu webový prohlížeč. Zobrazí se kód XML vrácený webovou službou a výsledky jakékoli operace.

## <a name="see-also"></a>Viz také

- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
