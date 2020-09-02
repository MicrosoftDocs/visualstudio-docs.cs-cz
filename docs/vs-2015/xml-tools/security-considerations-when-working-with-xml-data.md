---
title: Otázky zabezpečení při práci s daty XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 491e8cf8f9441180e66259ed295e04e8a1a90493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656138"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Aspekty zabezpečení při práci s daty XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje problémy se zabezpečením, o kterých potřebujete znát při práci s editorem XML nebo s ladicím programem XSLT.

## <a name="xml-editor"></a>Editor XML
 Editor XML je založen na textovém editoru sady Visual Studio. Spoléhá na <xref:System.Xml> třídy a a <xref:System.Xml.Xsl> zpracovává mnoho procesů XML.

- Transformace XSLT jsou spouštěny v nové doméně aplikace. Transformace XSLT jsou *v izolovaném prostoru (sandbox)*. To znamená, že se zásady zabezpečení přístupu k kódu vašeho počítače používají k určení omezených oprávnění na základě toho, kde se nachází šablona stylů XSLT. Například šablony stylů z internetového umístění mají nejvíc omezená oprávnění, zatímco šablony stylů zkopírované na pevný disk běží s úplným vztahem důvěryhodnosti.

- <xref:System.Xml.Xsl.XslCompiledTransform>Třída se používá ke KOMPILACI XSLT do Microsoft Intermediate Language pro rychlejší výkon během provádění.

- Schémata, která odkazují na externí umístění v souboru katalogu, se stáhnou automaticky při prvním načtení editoru XML. <xref:System.Xml.Schema.XmlSchemaSet>Třída se používá ke kompilaci schémat. Soubor katalogu, který je dodáván s editorem XML, nemá odkazy na žádná externí schémata. Uživatel musí explicitně přidat odkaz na externí schéma předtím, než Editor XML stáhne soubor schématu. Stahování HTTP se dá zakázat prostřednictvím stránky **Možnosti různých nástrojů** pro editor XML.

- Editor XML používá <xref:System.Net> třídy ke stažení schémat.

## <a name="xslt-debugger"></a>Ladicí program XSLT
 Ladicí program XSLT používá spravované moduly ladění a třídy sady Visual Studio z <xref:System.Xml> <xref:System.Xml.Xsl> oboru názvů a.

- Ladicí program XSLT spouští každou transformaci XSLT v doméně aplikace v izolovaném prostoru. Zásady zabezpečení přístupu k kódu vašeho počítače se používají k určení omezených oprávnění na základě toho, kde se nachází šablona stylů XSLT. Například šablony stylů z internetového umístění mají nejvíc omezená oprávnění, zatímco šablony stylů zkopírované na pevný disk běží s úplným vztahem důvěryhodnosti.

- Šablona stylů XSLT je kompilována pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.

- Filtr výrazu XSLT je načten spravovaným ladicím modulem. Spravovaný modul ladění předpokládá, že veškerý kód je spuštěn z místního počítače uživatele. <xref:System.Xml.Xsl.XslCompiledTransform>Třída proto stáhne soubor XSLT do místního počítače uživatele. Je možné, že dojde k omezení zvýšení oprávnění v privilegovaném provádění všech transformací XSLT v nové doméně aplikace s omezenými oprávněními.

## <a name="see-also"></a>Viz také
 [Aplikační domény](https://msdn.microsoft.com/39e57d07-a740-4cd4-ae82-e119ea3856c1)
