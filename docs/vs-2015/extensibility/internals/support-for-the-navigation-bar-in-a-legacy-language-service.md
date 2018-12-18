---
title: Podpora navigačního panelu ve službě starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81d2217be730803c1daedc37c3bac1a8d4154eea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804004"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Podpora navigačního panelu ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Navigační panel v horní části zobrazení editoru se zobrazí typy a členy v souboru. V levém rozevíracího seznamu jsou uvedeny typy a členy se zobrazí v pravém rozevíracího seznamu. Když uživatel vybere typ, blikající kurzor je umístěn na prvním řádku typu. Když uživatel vybere člena, blikající kurzor je umístěn v definici člena. Rozevírací seznamy jsou aktualizovány tak, aby odrážela aktuální umístění znaku stříšky.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Zobrazení a aktualizace na navigačním panelu  
 Pro podporu na navigačním panelu, musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy a implementovat <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody. Když vaše služba jazyka je uveden okno kódu, základní <xref:Microsoft.VisualStudio.Package.LanguageService> vytvoří instanci třídy <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, které se nachází <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objekt představující okno kódu. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Objekt potom bude mít nový <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektu. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Získá metoda <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu. Pokud vracet instanci vaší <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> volání vaše <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda k naplnění vnitřní seznamy a předá vaší <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozevírací panel správce. Rozevírací nabídky panelu Správce, volá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodu na vaše <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu k navázání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objekt, který obsahuje dva řádky rozevíracího seznamu.  
  
 Když přesune blikající kurzor <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> volání metod <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metoda. Základní <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> volání metod <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda ve vaší <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy k aktualizaci stavu na navigačním panelu. Předejte sadu <xref:Microsoft.VisualStudio.Package.DropDownMember> objekty v této metodě. Každý objekt představuje položku v rozevíracím seznamu.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Obsah na navigačním panelu  
 Na navigačním panelu obvykle obsahuje seznam typů a seznam členů. Seznam typů obsahuje všechny typy jsou dostupné v aktuálním zdrojovém souboru. Názvy typů obsahují informace dokončení oboru názvů. Následuje příklad kódu jazyka C# pomocí dvou typů:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Zobrazí seznam typů `TestLanguagePackage.TestLanguageService` a `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Seznam členů zobrazí dostupné členy typu, který je vybrán v seznamu typů. Pomocí výše uvedeného příkladu kódu, pokud `TestLanguagePackage.TestLanguageService` je typ, který je vybraný seznam členů by obsahovat soukromé členy `tokens` a `serviceName`. Interní `Token` se nezobrazí.  
  
 Můžete implementovat seznam členů tučným písmem názvu členem blikající kurzor umístíte dovnitř. Členy můžete také zobrazí v textu, zobrazena šedě označující, zda nejsou v rámci oboru, ve kterém je aktuálně kurzor.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Povolení podpory pro navigační panel  
 Chcete-li povolit podporu pro navigační panel, musíte nastavit `ShowDropdownBarOption` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut `true`. Tento parametr nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> vlastnost. Pro podporu na navigačním panelu, je nutné implementovat <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodu na <xref:Microsoft.VisualStudio.Package.LanguageService> třídy.  
  
 Ve vaší implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodu, pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> je nastavena na `true`, můžete se vrátit <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu. Pokud je objekt, se nezobrazí na navigačním panelu.  
  
 Možnost zobrazit na navigačním panelu můžete nastavit tímto uživatelem, takže je možné pro tento ovládací prvek resetovat, zatímco zobrazení pro editor je otevřený. Uživatel musí zavřít a znovu otevřete okno editoru předtím, než se změna proběhne.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementace podpora navigačního panelu  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Metoda přebírá dva seznamy (jeden pro každý rozevíracího seznamu) a dvě hodnoty představující aktuální výběr v seznamu. Seznamy a výběr hodnot je možné aktualizovat, v takovém případě <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda musí vracet `true` k označení, že došlo ke změně seznamu.  
  
 Jak se změní výběr v rozevíracím seznamu typů, seznam členů musí být aktualizovány tak, aby odrážely nový typ. Co se zobrazí v seznamu členů může být buď:  
  
- Seznam členů pro aktuální typ.  
  
- Všechny členy k dispozici ve zdrojovém souboru, ale se všemi členy není v aktuálním typem zobrazí šedě text. Uživatel může vybrat stále členy šedě, proto mohou být použity pro rychlou navigaci, ale barva znamená, že nejsou součástí aktuálně vybraného typu.  
  
  Implementace <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda obvykle provádí následující kroky:  
  
1.  Získání seznamu sad aktuální deklarace pro zdrojový soubor.  
  
     Existuje mnoho způsobů, jak naplnit seznamy. Jedním z přístupů je vytvořit vlastní metodu do vaší verze <xref:Microsoft.VisualStudio.Package.LanguageService> třídu, která volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu parse vlastní důvod, který vrátí seznam všech deklarací. Další možností je pravděpodobně volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody přímo z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodu parse vlastní důvod. Třetí přístup může být pro ukládání do mezipaměti deklarace v <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy vrácený poslední operaci úplné analýzy v <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a načíst z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
2.  Naplnění nebo aktualizujte seznam typů.  
  
     Seznam typů může aktualizovat při změně zdroje nebo pokud jste se rozhodli změnit styl textu typy založené na aktuální pozici blikajícího kurzoru. Všimněte si, že tuto pozici je předán <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.  
  
3.  Určení typů na výběr v seznamu typy založené na aktuální pozici blikajícího kurzoru.  
  
     Můžete hledat deklarace, které jste získali v kroku 1, abyste našli typ, který vloží aktuální pozici blikajícího kurzoru a pak vyhledejte typy seznamu pro daný typ k určení jeho index do seznamu typů.  
  
4.  Naplnění nebo aktualizaci seznamu členů podle vybraného typu.  
  
     Seznam členů odráží, co se nyní zobrazí **členy** rozevíracího seznamu. Obsah seznamu členů může třeba aktualizovat, pokud došlo ke změně zdroje nebo pokud zobrazujete pouze členy vybraného typu a vybraný typ se změnil. Pokud budete chtít zobrazit všechny členy ve zdrojovém souboru, styl textu každého člena v seznamu musí aktualizovat, pokud došlo ke změně aktuálně vybraného typu.  
  
5.  Zjistěte člena vyberte v seznamu členů podle aktuální pozici blikajícího kurzoru.  
  
     Hledání deklarací, které jste získali v kroku 1 pro člena, který obsahuje aktuální pozici blikajícího kurzoru a potom najděte seznam členů pro tento člen k určení jeho index do seznamu členů.  
  
6.  Vrátí `true` Pokud seznamy nebo výběrů v seznamech byly provedeny žádné změny.

