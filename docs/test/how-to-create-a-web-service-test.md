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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589094"
---
# <a name="how-to-create-a-web-service-test"></a>Postupy: vytvoření testu webové služby

Test výkonnosti webu můžete použít k otestování webové služby. S použitím **vložit žádost o** a **vložit žádost webové služby** možnosti, můžete přizpůsobit jednotlivé požadavky v **editoru testu výkonnosti webu** najít web stránky služby. Tyto stránky obvykle nejsou zobrazení ve webové aplikaci. Pro přístup k těmto stránkám je tedy nutné přizpůsobit požadavek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postupy používají webovou službu, která je obsažena v sadě Commerce Starter Kit. Můžete ji stáhnout [ASP.NET commerce starter kit](https://sourceforge.net/projects/ppcsk/).

**Požadavky**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>K otestování webové služby

1. Vytvoření nového testu výkonnosti webu. Poté, co v prohlížeči se otevře, zvolte **Zastavit**.

2. V **editoru testu výkonnosti webu**, klikněte pravým tlačítkem na test výkonnosti webu a vyberte **přidat požadavek webové služby**.

3. V **Url** vlastnosti nového požadavku zadejte název webové služby, například **http://localhost/storecsvs/InstantOrder.asmx** .

4. Otevřete samostatnou relaci prohlížeče a zadejte adresu URL *.asmx* stránku **adresu** nástrojů. Zvolte metodu, která má být testována, a prohlédněte si zprávu protokolu SOAP. Obsahuje hlavičku `SOAPAction`.

5. V **editoru testu výkonnosti webu**, klikněte pravým tlačítkem na žádost a vyberte **přidat hlavičku** přidáte novou hlavičku. V **název** vlastnost, typ `SOAPAction`. V **hodnotu** vlastnost, zadejte hodnotu, která se zobrazí v `SOAPAction`, jako například `"http://tempuri.org/CheckStatus"`.

6. Rozbalte uzel adresy URL v editoru, zvolte **tělo řetězce** uzel a **typ obsahu** vlastnosti zadejte hodnotu `text/xml`.

7. Vraťte se do prohlížeče v kroku 4, zvolte oddíl XML požadavku protokolu SOAP z stránku popisu webové služby a zkopírujte do schránky.

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

9. Vraťte se **editoru testu výkonnosti webu** a klikněte na tlačítko se třemi tečkami **(...)**  v **tělo řetězce** vlastnost. Vložte obsah schránky do vlastnosti.

10. Aby test proběhl úspěšně, je zapotřebí všechny zástupné hodnoty v kódu XML nahradit platnými hodnotami. V předchozí ukázce by byly nahrazeny dvě instance typu `string` a jedna typu `int`. Tato operace webové služby bude dokončena pouze v případě, že existuje registrovaný uživatel, který provedl objednávku.

11. Klikněte pravým tlačítkem na požadavek webové služby a vyberte **přidat parametr QueryString adresy URL**.

12. Parametru řetězce dotazu přiřaďte název a hodnotu. V předchozím příkladu je název `op` a hodnota je `CheckStatus`. Určuje, k provedení operace webové služby.

    > [!NOTE]
    > Vytváření datových vazeb můžete použít v těle zprávy protokolu SOAP s použitím nahradit libovolné zástupné hodnoty hodnotami vázaných `{{DataSourceName.TableName.ColumnName}}` syntaxe.

13. Spusťte test. V horním podokně **prohlížeče výsledků testu výkonnosti webu**, vyberte požadavek webové služby. V dolním podokně vyberte kartu webový prohlížeč. Zobrazí se kód XML vrácený webovou službou a výsledky jakékoli operace.

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
