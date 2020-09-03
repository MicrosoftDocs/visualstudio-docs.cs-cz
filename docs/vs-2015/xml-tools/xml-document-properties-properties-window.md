---
title: Vlastnosti dokumentu XML, okno vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669509"
---
# <a name="xml-document-properties-properties-window"></a>Vlastnosti dokumentu XML, okno Vlastnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **vlastnosti** poskytuje základní informace o dokumentu, který je aktivní v editoru XML. Vlastnosti, které jsou k dispozici, se liší v závislosti na typu dokumentu XML, který je aktuálně aktivní.

> [!NOTE]
> Všechny vlastnosti dokumentu XML jsou uloženy v řešení. V důsledku toho není nutné znovu zadávat tyto hodnoty při příštím otevření řešení.

 **Kódování** Kódování znaků souboru. Změna této vlastnosti také změní atribut Encoding v deklaraci XML a naopak. Nové kódování se použije ke kódování souboru při uložení souboru.

 **Vstup** Vstupní dokument přidružený k šabloně stylů XSLT. Používá ho příkaz **ShowXSLT Output** . Dokument lze vybrat pomocí tlačítka Procházet (**...**).

 Tato vlastnost je viditelná pouze v případě, že je soubor XSLT aktuálně aktivní v okně editoru.

 **Výstup** Soubor, který je generován při transformaci dokumentu XML.

 Pokud není zadán soubor, je vygenerován výchozí název souboru založený na `method` atributu `xsl:output` elementu, který určuje příponu souboru. Výchozí soubor se nachází v dočasném adresáři aktuálního uživatele.

 **Schémata** Schémata, která se mají použít pro ověření Tlačítko otevře dialogové okno **schémata XSD** , které lze použít k výběru schémat, která chcete použít.

 Můžete také zadat cestu k schématům. Pokud je zadáno více schémat, je nutné každou cestu schématu uzavřít do dvojitých uvozovek.

 **Šablona stylů** Soubor XSLT, který se používá k transformaci dokumentu při použití příkazu **Zobrazit výstup XSLT** . Pokud je toto pole prázdné, pokud je použit příkaz **Zobrazit výstup XSLT** , používá editor hodnotu poskytnutou v `xml-stylesheet` pokynech pro zpracování dokumentu nebo vás vyzve k zadání názvu souboru.

 Při úpravách souboru XSLT lze tuto vlastnost použít k určení, zda má být použita jiná šablona stylů, pokud je vybrán příkaz **Zobrazit výstup XSLT** nebo **ladění XSLT** . Můžete to třeba udělat, když upravujete šablonu stylů, která je obsažena v nadřazené šabloně stylů.

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md) – [komponenty editoru XML](../xml-tools/xml-editor-components.md)
