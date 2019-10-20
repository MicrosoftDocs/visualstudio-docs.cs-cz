---
title: 'Postupy: úprava souborů XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670874"
---
# <a name="how-to-edit-xml-files"></a>Postupy: úprava souborů XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML je nový editor pro soubory XML. Dá se použít v samostatném souboru XML nebo v souboru přidruženém k projektu sady Visual Studio. Editor XML je přidružen k následujícím příponám souborů:. config,. DTD,. XML,. xsd,. XDR,. XSL,. XSLT a. vssettings. Editor XML je také přidružen k jinému typu souboru, který nemá registrován žádný konkrétní editor a který obsahuje obsah XML nebo DTD.

> [!NOTE]
> Dokumenty XHTML jsou zpracovávány editorem HTML.

### <a name="to-edit-an-xml-file"></a>Úprava souboru XML

1. Dvakrát klikněte na soubor, který chcete upravit.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Přidání nového souboru XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. V podokně **šablony** vyberte **soubor XML** .

3. Do pole **název** zadejte název souboru a stiskněte **Přidat**.

     Soubor XML se přidá do projektu a otevře se v editoru XML. Soubor obsahuje výchozí deklaraci XML `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Přidání existujícího souboru XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat existující položku**.

     Zobrazí se dialogové okno **Přidat existující položku** .

2. Vyberte soubor XML a stiskněte **Přidat**.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Vytvoření nového souboru XML nebo XSLT

1. V nabídce **soubor** vyberte možnost **Nový**.

     Zobrazí se dialogové okno **nový soubor** .

2. Vyberte **soubor XML** , chcete-li vytvořit nový soubor XML; nebo vyberte **soubor XSLT** pro vytvoření nové šablony stylů XSLT.

3. Klikněte na **otevřít**.

### <a name="to-create-a-project-for-xml-files"></a>Vytvoření projektu pro soubory XML

1. V nabídce **soubor** vyberte **Nový**a pak vyberte **projekt**.

     Zobrazí se dialogové okno **Nový projekt** .

2. Vyberte jazyk kódu, který chcete zvolit, vyberte **prázdný projekt**a klikněte na **OK**.

3. Přidejte soubory XML do projektu.

     Editor XML vyhledá schémata, která přidáte do tohoto projektu, a použije je pro ověřování a IntelliSense v jakémkoli souboru XML, schématu nebo souboru XSLT, které upravíte v otevřeném projektu.

## <a name="see-also"></a>Viz také
 XML [editoru XML](../xml-tools/xml-editor.md) – [Vlastnosti dokumentu v okně Vlastnosti](../xml-tools/xml-document-properties-properties-window.md) [: vytvoření schématu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
