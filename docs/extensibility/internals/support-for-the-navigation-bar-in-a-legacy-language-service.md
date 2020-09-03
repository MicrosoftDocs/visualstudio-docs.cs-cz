---
title: Podpora pro navigační panel ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704866"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Podpora navigačního panelu ve službě starší verze jazyka
Navigační panel v horní části zobrazení editoru zobrazuje typy a členy v souboru. Typy jsou zobrazeny v levém rozevíracím seznamu a členové jsou zobrazeni v rozevíracím seznamu vpravo. Když uživatel vybere typ, kurzor se umístí na první řádek typu. Když uživatel vybere člena, kurzor se umístí na definici člena. Rozevírací seznamy jsou aktualizovány tak, aby odrážely aktuální umístění blikajícího kurzoru.

## <a name="displaying-and-updating-the-navigation-bar"></a>Zobrazení a aktualizace navigačního panelu
 Chcete-li podporovat navigační panel, musíte odvodit třídu z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy a implementovat <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodu. Pokud má služba jazyka uděleno okno kódu, třída Base vytvoří <xref:Microsoft.VisualStudio.Package.LanguageService> instanci <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , která obsahuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objekt reprezentující okno kódu. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Objektu se pak přidaný nový <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Metoda získá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt. Pokud vrátíte instanci vaší <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> volání <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody naplní interní seznamy a předá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Správci rozevíracího panelu. Správce rozevíracích panelů pak zavolá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu pro vytvoření <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objektu, který obsahuje dva rozevírací panely.

 Při přesunutí blikajícího kurzoru <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> metoda volá <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodu. Základní <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metoda volá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodu ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídě, aby aktualizovala stav navigačního panelu. Této metodě předáte sadu <xref:Microsoft.VisualStudio.Package.DropDownMember> objektů. Každý objekt představuje položku v rozevíracím seznamu.

## <a name="the-contents-of-the-navigation-bar"></a>Obsah navigačního panelu
 Navigační panel obvykle obsahuje seznam typů a seznam členů. Seznam typů obsahuje všechny typy, které jsou k dispozici v aktuálním zdrojovém souboru. Názvy typů obsahují informace o kompletním oboru názvů. Následuje příklad kódu jazyka C# se dvěma typy:

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

 Seznam typ se zobrazí `TestLanguagePackage.TestLanguageService` a `TestLanguagePackage.TestLanguageService.Tokens` .

 Seznam Členové zobrazí dostupné členy typu, který je vybrán v seznamu typy. Při použití výše uvedeného příkladu kódu, pokud `TestLanguagePackage.TestLanguageService` je vybraný typ, by seznam členů obsahoval soukromé členy `tokens` a `serviceName` . Vnitřní struktura `Token` se nezobrazí.

 Seznam členů můžete implementovat, chcete-li název člena označit tučně, když je kurzor umístěn uvnitř něj. Členy lze také zobrazit v šedě zobrazeném textu, což značí, že nejsou v rámci oboru, ve kterém je aktuálně umístěn blikající kurzor.

## <a name="enabling-support-for-the-navigation-bar"></a>Povolení podpory pro navigační panel
 Chcete-li povolit podporu pro navigační panel, je nutné nastavit `ShowDropdownBarOption` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributu na `true` . Tento parametr nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> vlastnost. Chcete-li podporovat navigační panel, je nutné implementovat <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt v <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodě <xref:Microsoft.VisualStudio.Package.LanguageService> třídy.

 V implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metody, pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> je vlastnost nastavena na `true` , můžete vrátit <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt. Pokud objekt nevrátíte, navigační panel se nezobrazí.

 Možnost Zobrazit navigační panel může nastavit uživatel, takže je možné, že tento ovládací prvek bude resetován, dokud je otevřeno zobrazení editoru. Uživatel musí zavřít okno editoru a znovu ho otevřít, aby se změna projevila.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementace podpory pro navigační panel
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Metoda přijímá dva seznamy (jeden pro každý rozevírací seznam) a dvě hodnoty představující aktuální výběr v jednotlivých seznamech. Seznamy a hodnoty výběru lze aktualizovat. v takovém případě <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> musí metoda vracet, `true` aby označovala, že se seznamy změnily.

 Při změně výběru v rozevíracím seznamu typy musí být seznam členů aktualizován tak, aby odrážel nový typ. To, co se zobrazuje v seznamu členů, může mít jednu z těchto hodnot:

- Seznam členů pro aktuální typ.

- Všichni členové, kteří jsou k dispozici ve zdrojovém souboru, ale se všemi členy, kteří nejsou v aktuálním typu zobrazeném v textu šedě. Uživatel stále může vybrat šedě zobrazené členy, aby je bylo možné použít k rychlé navigaci, ale barva označuje, že nejsou součástí aktuálně vybraného typu.

  Implementace <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody obvykle provádí následující kroky:

1. Získá seznam aktuálních deklarací pro zdrojový soubor.

     Seznam obsahuje několik způsobů, jak seznamy naplnit. Jedním z možností je vytvořit vlastní metodu ve vaší verzi <xref:Microsoft.VisualStudio.Package.LanguageService> třídy, která volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu s vlastním důvodem analýzy, který vrací seznam všech deklarací. Jiným přístupem může být volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody přímo z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody s vlastním důvodem analýzy. Třetí přístup může být Uložit deklarace do mezipaměti ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídě vrácené poslední operací analýzy ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě a načíst z <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody.

2. Naplnit nebo aktualizovat seznam typů.

     Obsah seznamu typů se může aktualizovat, když se změnil zdroj, nebo pokud jste se rozhodli změnit styl textu typů na základě aktuální pozice blikajícího kurzoru. Všimněte si, že tato pozice je předána <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodě.

3. Určete typ, který se má vybrat v seznamu typů na základě aktuální pozice blikajícího kurzoru.

     Můžete vyhledat deklarace, které byly získány v kroku 1, a vyhledat tak typ, který obklopuje aktuální pozici blikajícího kurzoru, a potom v seznamu typů vyhledat daný typ pro určení jeho indexu v seznamu typů.

4. Naplní nebo aktualizuje seznam členů na základě vybraného typu.

     Seznam členů odráží, co se aktuálně zobrazuje v rozevíracím seznamu **Členové** . Obsah seznamu členů může být potřeba aktualizovat, pokud se změnil zdroj nebo pokud zobrazujete jenom členy vybraného typu a vybraný typ se změnil. Pokud se rozhodnete zobrazit všechny členy ve zdrojovém souboru, je nutné aktualizovat textový styl každého člena v seznamu, pokud se aktuálně vybraný typ změnil.

5. Určete člena, který se má vybrat v seznamu členů na základě aktuální pozice blikajícího kurzoru.

     V deklaracích, které byly získány v kroku 1 pro člena, který obsahuje aktuální pozici blikajícího kurzoru, prohledejte seznam členů pro daného člena a určete jeho index na seznam členů.

6. Vrátí se, `true` Pokud byly v seznamech provedeny nějaké změny, nebo výběry v obou seznamech.
