---
title: 'Postupy: úprava souborů XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd8671bf45230ec24a37d5006a2d32e5aabe8f28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645927"
---
# <a name="how-to-edit-xml-files"></a>Postupy: úprava souborů XML

Editor XML je nový editor pro soubory XML. Dá se použít v samostatném souboru XML nebo v souboru přidruženém k projektu sady Visual Studio. Editor XML je přidružen k následujícím příponám souborů: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT*a *. vssettings*. Editor XML je také přidružen k jinému typu souboru, který nemá registrován žádný konkrétní editor a který obsahuje obsah XML nebo DTD.

> [!NOTE]
> Dokumenty XHTML jsou zpracovávány editorem HTML.

Chcete-li upravit soubor XML, dvakrát klikněte na soubor, který chcete upravit.

## <a name="add-a-new-xml-file-to-a-project"></a>Přidat nový soubor XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. V podokně **šablony** vyberte **soubor XML** .

3. Do pole **název** zadejte název souboru a stiskněte **Přidat**.

   Soubor XML se přidá do projektu a otevře se v editoru XML. Soubor obsahuje výchozí deklaraci XML `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Přidat existující soubor XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat existující položku**.

   Zobrazí se dialogové okno **Přidat existující položku** .

2. Vyberte soubor XML a stiskněte **Přidat**.

## <a name="create-a-new-xml-or-xslt-file"></a>Vytvořit nový soubor XML nebo XSLT

1. V nabídce **soubor** vyberte možnost **Nový**.

   Zobrazí se dialogové okno **nový soubor** .

2. Vyberte **soubor XML** , chcete-li vytvořit nový soubor XML; nebo vyberte **soubor XSLT** pro vytvoření nové šablony stylů XSLT.

3. Klikněte na **otevřít**.

## <a name="create-an-empty-project-for-xml-files"></a>Vytvoření prázdného projektu pro soubory XML

::: moniker range="vs-2017"

1. V nabídce **soubor** vyberte **Nový** > **projekt**.

   Zobrazí se dialogové okno **Nový projekt** .

2. Vyberte jazyk kódu, který chcete zvolit, a pak vyberte šablonu **prázdného projektu (.NET Framework)** .

3. Klikněte na tlačítko **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce **soubor** vyberte **Nový** > **projekt**.

2. Do vyhledávacího pole šablony zadejte **prázdný projekt** , vyberte šablonu **prázdného projektu (.NET Framework)** a pak klikněte na **Další**.

3. Klikněte na **vytvořit**.

::: moniker-end

4. Přidejte soubory XML do projektu.

   Editor XML vyhledá schémata, která přidáte do tohoto projektu, a použije je pro ověřování a IntelliSense v jakémkoli souboru XML, schématu nebo souboru XSLT, které upravíte v otevřeném projektu.

## <a name="see-also"></a>Viz také:

- [Editor XML](../xml-tools/xml-editor.md)
- [Vlastnosti dokumentu XML, okno vlastností](../xml-tools/xml-document-properties-properties-window.md)
- [Postupy: vytvoření schématu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)