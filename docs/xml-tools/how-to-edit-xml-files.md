---
title: 'Postupy: Úpravy souborů XML'
ms.date: 11/04/2016
description: Naučte se, jak pomocí editoru XML v sadě Visual Studio upravovat soubory, které obsahují obsah XML nebo DTD.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c538e9a4da3c4bbd08c571818dbaaaca466c2471
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948541"
---
# <a name="how-to-edit-xml-files"></a>Postupy: úprava souborů XML

Editor XML je nový editor pro soubory XML. Dá se použít v samostatném souboru XML nebo v souboru přidruženém k projektu sady Visual Studio. Editor XML je přidružen k následujícím příponám souborů: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT* a *. vssettings*. Editor XML je také přidružen k jinému typu souboru, který nemá registrován žádný konkrétní editor a který obsahuje obsah XML nebo DTD.

> [!NOTE]
> Dokumenty XHTML jsou zpracovávány editorem HTML.

Chcete-li upravit soubor XML, otevřete soubor, který chcete upravit.

## <a name="add-a-new-xml-file-to-a-project"></a>Přidat nový soubor XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. V podokně **šablony** vyberte **soubor XML** .

3. Do pole **název** zadejte název souboru a stiskněte **Přidat**.

   Soubor XML se přidá do projektu a otevře se v editoru XML. Soubor obsahuje výchozí deklaraci XML, `<?xml version="1.0" encoding="utf-8" ?>` .

## <a name="add-an-existing-xml-file-to-a-project"></a>Přidat existující soubor XML do projektu

1. V nabídce **projekt** vyberte možnost **Přidat existující položku**.

   Zobrazí se dialogové okno **Přidat existující položku** .

2. Vyberte soubor XML a stiskněte **Přidat**.

## <a name="create-a-new-xml-or-xslt-file"></a>Vytvořit nový soubor XML nebo XSLT

1. V nabídce **soubor** vyberte možnost **Nový**.

   Zobrazí se dialogové okno **nový soubor** .

2. Vyberte **soubor XML** , chcete-li vytvořit nový soubor XML; nebo vyberte **soubor XSLT** pro vytvoření nové šablony stylů XSLT.

3. Vyberte **Otevřít**.

## <a name="create-an-empty-project-for-xml-files"></a>Vytvoření prázdného projektu pro soubory XML

::: moniker range="vs-2017"

1. V nabídce **soubor** vyberte možnost **Nový** > **projekt**.

   Zobrazí se dialogové okno **Nový projekt**.

2. Vyberte jazyk kódu, který chcete zvolit, a pak vyberte šablonu **prázdného projektu (.NET Framework)** .

3. Vyberte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce **soubor** vyberte možnost **Nový** > **projekt**.

2. Do vyhledávacího pole šablony zadejte **prázdný projekt** , vyberte šablonu **prázdného projektu (.NET Framework)** a pak vyberte **Další**.

3. Vyberte **Vytvořit**.

::: moniker-end

4. Přidejte soubory XML do projektu.

   Editor XML vyhledá schémata, která přidáte do tohoto projektu, a použije je pro ověřování a IntelliSense v jakémkoli souboru XML, schématu nebo souboru XSLT, které upravíte v otevřeném projektu.

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
- [Vlastnosti dokumentu XML, okno vlastností](../xml-tools/xml-document-properties-properties-window.md)
- [Postupy: vytvoření schématu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
