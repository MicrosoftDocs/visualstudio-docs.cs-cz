---
title: Ochrana dokumentů v řešeních na úrovni dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22c8f135770fbd427d361b9c9b113da3b20e609a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447866"
---
# <a name="document-protection-in-document-level-solutions"></a>Ochrana dokumentů v řešeních na úrovni dokumentu
  Můžete využívat funkce ochrany aplikace Microsoft Office Word a Microsoft Office Excel v projekty na úrovni dokumentu. Tyto funkce brání neoprávněným uživatelům v provádění změn chráněných části dokumentu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Pomocí aplikace Excel, můžete zapnout ochranu zapnout a vypnout sešit je otevřen v návrháři. Použití aplikace Word, můžete zapnout ochranu pouze mimo designer. Za běhu můžete povolit nebo zakázat ochranu prostřednictvím kódu programu pro Word a Excel.  
  
 Pokud je ochrana dokumentu v dokumentu, který je otevřít v Návrháři povoleno, všechny ovládací prvky jsou odebrány z **sada nástrojů** nebo nebudou k dispozici, a nelze přetáhnout nic z **zdroje dat** okna dokumentu.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument a chráněné dokumenty  
 Pokud je dokument chráněný, datové mezipaměti není přístupná z mimo dokumentu. Nelze použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy načíst nebo pracovat s daty, která se uloží do mezipaměti v chráněný dokument, nebo pomocí jiných metod <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> třídy.  
  
## <a name="word-document-protection-in-the-designer"></a>Ochrana dokumentů aplikace Word v Návrháři  
 Pokud přidáte ochrany na dokument aplikace Word nebo šablonu je otevřen v sadě Visual Studio, nelze spustit, vynucovat ochranu v návrháři. Dokument je v režimu návrhu, když je otevřen v sadě Visual Studio, a musí být v spuštěn režimu předtím, než můžete začít vynucovat ochranu.  
  
 Pokud vytvoříte projekt, který používá stávající dokument aplikace Word, který má zapnutou ochranu, je dokument chráněný otevřené v návrháři. Nelze upravit části chráněného dokumentu, ale můžete pořád psaní kódu v editoru kódu k automatizaci dokumentu. Můžete také nemůže vytvořit projekt Pokud je povolena ochrana dokumentu je otevřen v sadě Visual Studio.  
  
 Můžete vypnout ochranu dokumentu je otevřen v návrháři, aby mohli dokument upravovat a sestavte projekt. Ochranu pro kopírování v Návrháři nelze vypnout, při ladění; dokument, který otevře během ladění je samostatná kopie z jedné otevřít v Návrháři (kopie výstup je uložena v *\bin* adresáři v jazyce Visual Basic a *\bin\debug* adresář pro jazyk C#).  
  
 Můžete povolit ochranu na kopii dokumentu, které se otevře v Návrháři zavřít projekt v sadě Visual Studio, otevřením kopii dokumentu, který je v adresáři projektu a zapnutí ochrany.  
  
## <a name="enforce-word-document-protection-on-build"></a>Vynutit ochrana dokumentů aplikace Word na sestavení  
 Visual Studio spustí, vynucovat ochranu dokumentů aplikace Word a šablony během procesu sestavení tak, aby po otevření dokumentu pro ladění zapnutá ochrana. Je dokument chráněný pomocí prázdné heslo.  
  
 Ochrana je povolena při sestavování proto, pokud je kód v dokumentu <xref:Microsoft.Office.Tools.Word.Document.Startup> událost, která může způsobit, že výjimky nebo změnit chování aplikace, tento kód může být vyladěnou správně. Pokud povolíte ochranu po otevření dokumentu, inicializace kód nelze ladit nebo testována.  
  
## <a name="setting-the-password"></a>Nastavení hesla  
 Visual Studio automaticky povolí ochranu, ale poskytuje ve výchozím nastavení žádné heslo. Pokud chcete, aby ochrana dokumentu heslo, musíte jej přidat před nasazením řešení. Přidání hesla umožňuje autorizovaným uživatelům odebrání ochrany dokumentu. bez zadání hesla nelze snadno odebrat ochranu. Podrobnosti o nastavení hesla, najdete v tématu nápovědy v konkrétní aplikaci Office.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zamykání dokumentů a částí dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md)   
 [Přehled rozšíření spravovaného kódu a Správa přístupových práv](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)   
 [Postupy: povolení kód pro spuštění pozadí dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)  
  
  