---
title: Spustit transformaci XSLT
description: Naučte se, jak pomocí editoru XML přidružit šablonu stylů XSLT k dokumentu XML, provést transformaci XSLT a zobrazit výstup.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1c7165f301c82dfaf5aa066a3e15bd7ab244089
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970242"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Postupy: spuštění transformace XSLT z editoru XML

Editor XML umožňuje přidružit šablonu stylů XSLT k dokumentu XML, provést transformaci a zobrazit výstup. Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.

Vlastnost **Output** Určuje název souboru pro výstup. Pokud je vlastnost **Output** prázdná, v dočasném adresáři se vygeneruje název souboru. Přípona souboru je založena na `xsl:output` elementu v šabloně stylů a může být.*XML*,. *txt* nebo. *htm*.

Pokud **výstupní** vlastnost určuje název souboru s příponou. *htm* nebo. *HTML* rozšíření, výstup XSLT je zobrazený ve webovém prohlížeči. Všechny ostatní přípony souborů jsou otevřeny pomocí výchozího editoru zvoleného v aplikaci Visual Studio. Například pokud je přípona souboru. *XML*, Visual Studio používá editor XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Spuštění transformace XSLT ze souboru XML

1. Otevřete dokument XML v editoru XML.

2. Přidružte šablonu stylů XSLT k dokumentu XML.

    - Přidejte `xml-stylesheet` do dokumentu XML instrukci pro zpracování. Do prologu dokumentu přidejte například následující řádek: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       -nebo-

    - Přidejte šablonu stylů XSLT pomocí okna **vlastnosti** . Otevřete-li soubor XML v editoru, klikněte pravým tlačítkem myši kdekoli v editoru a vyberte možnost **vlastnosti**. V okně **vlastnosti** klikněte na pole se **šablonou stylů** a vyberte tlačítko Procházet (...). Vyberte šablonu stylů XSLT a pak zvolte **otevřít**.

3. Na panelu nabídek vyberte **XML**  >  **Spustit XSLT bez ladění**. Nebo stiskněte klávesy **CTRL** + **ALT** + **F5**.

   Výstup z transformace XSLT se zobrazí v novém okně dokumentu.

   > [!NOTE]
   > Pokud k dokumentu XML není přidružena žádná šablona stylů, zobrazí se dialogové okno s výzvou, abyste zadali šablonu stylů, která se má použít.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Provede transformaci XSLT ze šablony stylů XSLT.

1. Otevřete šablonu stylů XSLT v editoru XML.

2. Zadejte dokument XML do pole **vstup** v okně **vlastností** dokumentu.

   > [!NOTE]
   > Dokument XML je vstupní dokument, který se používá pro transformaci. Pokud při spuštění transformace XSLT není dokument zadán, zobrazí se dialogové okno **otevřít soubor** a v tomto okamžiku můžete zadat dokument.

3. Na panelu nabídek vyberte **XML**  >  **Spustit XSLT bez ladění**. Nebo stiskněte klávesy **CTRL** + **ALT** + **F5**.

   Výstup z transformace XSLT se zobrazí v novém okně dokumentu.

## <a name="specify-an-output-file-name"></a>Zadat název výstupního souboru

Můžete zadat název výstupního souboru pro soubory XML a XSL. Otevřete okno **vlastnosti** a zadejte název souboru do pole **výstup** .

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
