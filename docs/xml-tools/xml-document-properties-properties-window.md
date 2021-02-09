---
title: Vlastnosti dokumentu XML, okno Vlastnosti
description: Přečtěte si o vlastnostech dokumentu XML v okno Vlastnosti, které poskytují základní informace o aktivním dokumentu v editoru XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e12118f2f7f5d9189ca768f7be65a35b490eb54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875013"
---
# <a name="xml-document-properties-properties-window"></a>Vlastnosti dokumentu XML, okno Vlastnosti

Okno **vlastnosti** poskytuje základní informace o dokumentu, který je aktivní v editoru XML. Vlastnosti, které jsou k dispozici, se liší v závislosti na typu dokumentu XML, který je aktuálně aktivní.

> [!NOTE]
> Všechny vlastnosti dokumentu XML jsou uloženy v řešení. V důsledku toho není nutné znovu zadávat tyto hodnoty při příštím otevření řešení.

**Kódování**

Kódování znaků souboru. Změna této vlastnosti také změní atribut Encoding v deklaraci XML a naopak. Nové kódování se použije ke kódování souboru při uložení souboru.

**Vstup**

Vstupní dokument přidružený k šabloně stylů XSLT. Je používán příkazy **Spustit XSLT** , například **XML**  >  **spustí XSLT bez ladění**. Dokument lze vybrat pomocí tlačítka Procházet (**...**).

Tato vlastnost je viditelná pouze v případě, že je soubor XSLT otevřen v editoru.

**Výstup**

Soubor, který je generován při transformaci dokumentu XML.

Pokud není zadán soubor, je vygenerován výchozí název souboru založený na `method` atributu `xsl:output` elementu, který určuje příponu souboru. Výchozí soubor se nachází v dočasném adresáři aktuálního uživatele.

**Schémata**

Schémata, která se mají použít pro ověření Tlačítko otevře dialogové okno **schémata XSD** , které lze použít k výběru schémat, která chcete použít.

Můžete také zadat cestu k schématům. Pokud je zadáno více schémat, je nutné každou cestu schématu uzavřít do dvojitých uvozovek.

**Šablony**

Soubor XSLT, který se používá k transformaci dokumentu při **spuštění ladění XSLT** a **spuštění XSLT bez** příkazů pro ladění. Pokud je toto pole prázdné, použije editor hodnotu poskytnutou v `xml-stylesheet` dokumentu instrukcí pro zpracování nebo se zobrazí výzva k zadání názvu souboru.

Při úpravách souboru XSLT lze pomocí této vlastnosti určit, že by měla být použita jiná šablona stylů, pokud je vybrána možnost **Spustit ladění XSLT** nebo **Spustit XSLT bez příkazu ladit** . Můžete to třeba udělat, když upravujete šablonu stylů, která je obsažena v nadřazené šabloně stylů.

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
