---
title: Ochrana dokumentů v řešeních na úrovni dokumentu
description: Přečtěte si, jak můžete používat funkce ochrany systém Microsoft Office Word a systém Microsoft Office Excel v projektech na úrovni dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2898781a3603e7cb9582d246e4fa7edaaf6bddb9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846191"
---
# <a name="document-protection-in-document-level-solutions"></a>Ochrana dokumentů v řešeních na úrovni dokumentu
  Můžete použít funkce ochrany aplikace systém Microsoft Office Word a systém Microsoft Office Excel v projektech na úrovni dokumentu. Tyto funkce blokují neoprávněným uživatelům provádění změn v chráněných částech dokumentu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Pomocí aplikace Excel můžete zapnout nebo vypnout ochranu, zatímco je sešit otevřený v návrháři. Pomocí aplikace Word můžete ochranu zapnout pouze mimo návrháře. V době běhu můžete ochranu povolit nebo zakázat programově pro Word a Excel.

 Je-li povolena ochrana dokumentu v dokumentu, který je otevřen v návrháři, jsou všechny ovládací prvky odebrány z **panelu nástrojů** nebo nejsou k dispozici, a nelze přetáhnout cokoli z okna **zdroje dat** do dokumentu.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument a chráněné dokumenty
 Pokud je dokument chráněný, k datové mezipaměti nelze přistupovat mimo dokument. Třídu nelze použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> k načtení nebo manipulaci s daty, která jsou uložena v mezipaměti v chráněném dokumentu, nebo použijte jiné metody <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy.

## <a name="word-document-protection-in-the-designer"></a>Ochrana dokumentu aplikace Word v Návrháři
 Pokud přidáte ochranu k dokumentu nebo šabloně aplikace Word, je-li otevřen v aplikaci Visual Studio, nelze začít s vynucováním ochrany v návrháři. Dokument je v režimu návrhu, pokud je otevřen v aplikaci Visual Studio a musí být v režimu spuštění, aby bylo možné začít vynucování ochrany.

 Pokud však vytvoříte projekt, který používá existující dokument aplikace Word, který má zapnutou ochranu, dokument bude při otevření v Návrháři chráněn. Chráněné části dokumentu nemůžete upravit, ale přesto můžete napsat kód v editoru kódu pro automatizaci dokumentu. Nemůžete také sestavit projekt, pokud je ochrana povolena, když je dokument otevřen v aplikaci Visual Studio.

 Ochranu můžete zapnout i v případě, že dokument je otevřený v návrháři, takže můžete dokument upravit a sestavit projekt. Ochranu pro kopii v Návrháři nemůžete při ladění vypnout. dokument, který se otevře během ladění, je samostatná kopie od otevření v Návrháři (výstupní kopie je uložená v adresáři *\Bin* pro Visual Basic a v adresáři *\bin\debug* pro C#).

 Ochranu můžete povolit na kopii dokumentu, která se otevře v Návrháři tím, že projekt zavřete v aplikaci Visual Studio, otevřete kopii dokumentu, který se nachází v adresáři projektu, a zapnete ochranu.

## <a name="enforce-word-document-protection-on-build"></a>Vymáhat ochranu wordového dokumentu při sestavení
 Visual Studio spustí vynucování ochrany dokumentů a šablon aplikace Word během procesu sestavení, takže ochrana je povolena, když se dokument otevře pro ladění. Dokument je chráněn s prázdným heslem.

 Ochrana je povolena během sestavování, takže pokud je v události dokumentu kód <xref:Microsoft.Office.Tools.Word.Document.Startup> , který může způsobit výjimky nebo změnit chování aplikace, tento kód lze ladit správně. Pokud povolíte ochranu po otevření dokumentu, inicializační kód nelze ladit nebo testovat.

## <a name="setting-the-password"></a>Nastavení hesla
 Visual Studio automaticky povolí ochranu, ale ve výchozím nastavení neposkytuje žádné heslo. Pokud chcete, aby Ochrana dokumentu měla heslo, je nutné ji přidat před nasazením řešení. Přidání hesla vám umožní povolit oprávněným uživatelům odebrat ochranu dokumentu. bez hesla nelze ochranu snadno odebrat. Podrobnosti o nastavení hesla najdete v nápovědě v konkrétní aplikaci Office.

## <a name="see-also"></a>Viz také
- [Postupy: ochrana dokumentů a částí dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Přehled správy přístupových práv k informacím a rozšíření spravovaného kódu](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)
- [Postupy: povolení spuštění kódu na pozadí dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
