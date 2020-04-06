---
title: Podpora navigačního panelu ve službě staršího jazyka | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704866"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Podpora navigačního panelu ve službě starší verze jazyka
Navigační panel v horní části zobrazení editoru zobrazuje typy a členy v souboru. Typy jsou zobrazeny v levém rozevíracím seznamu a členy jsou zobrazeny v pravém rozevíracím seznamu. Když uživatel vybere typ, stříška je umístěna na prvním řádku typu. Když uživatel vybere člena, stříška je umístěn na definici člena. Rozevírací seznamy jsou aktualizovány tak, aby odrážely aktuální umístění stříšky.

## <a name="displaying-and-updating-the-navigation-bar"></a>Zobrazení a aktualizace navigačního panelu
 Pro podporu navigačního panelu je nutné <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> odvodit třídu z třídy a implementovat metodu. <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Když je službě jazyka přiděleno okno <xref:Microsoft.VisualStudio.Package.LanguageService> kódu, základní <xref:Microsoft.VisualStudio.Package.CodeWindowManager>třída vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instance , která obsahuje objekt představující okno kódu. Objekt <xref:Microsoft.VisualStudio.Package.CodeWindowManager> je pak uveden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nový objekt. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> získá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objekt. Pokud vrátíte instanci <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> vaší <xref:Microsoft.VisualStudio.Package.CodeWindowManager> třídy, zavolá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodu k <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> naplnění [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vnitřníseznamy a předá objekt správce rozevíracího panelu. Správce rozevíracího panelu zase volá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> k vytvoření objektu, který obsahuje dva rozevírací panely.

 Když se stříška <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> přesune, metoda volá metodu. Základní <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metoda volá <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ve vaší třídě k aktualizaci stavu navigačního panelu. Tuto metodu <xref:Microsoft.VisualStudio.Package.DropDownMember> předáte sadu objektů. Každý objekt představuje položku v rozevíracím souboru.

## <a name="the-contents-of-the-navigation-bar"></a>Obsah navigačního panelu
 Navigační panel obvykle obsahuje seznam typů a seznam členů. Seznam typů obsahuje všechny typy, které jsou k dispozici v aktuálním zdrojovém souboru. Názvy typů zahrnují úplné informace o oboru názvů. Následuje příklad kódu jazyka C# se dvěma typy:

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

 Zobrazí se seznam `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens`typů a .

 Seznam členů zobrazuje dostupné členy typu vybraného v seznamu typů. Pomocí výše uvedeného `TestLanguagePackage.TestLanguageService` příkladu kódu, pokud je vybraný typ, `tokens` seznam `serviceName`členů bude obsahovat soukromé členy a . Vnitřní struktura `Token` není zobrazena.

 Můžete implementovat seznam členů, aby se název člena tučně, když je stříška umístěna uvnitř. Členy lze také zobrazit v šedě zobrazený text, označující, že nejsou v oboru, kde je stříška aktuálně umístěna.

## <a name="enabling-support-for-the-navigation-bar"></a>Povolení podpory navigačního panelu
 Chcete-li povolit podporu navigačního `ShowDropdownBarOption` panelu, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musíte `true`nastavit parametr atributu na . Tento parametr <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> nastaví vlastnost. Pro podporu navigačního panelu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> je nutné <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> implementovat <xref:Microsoft.VisualStudio.Package.LanguageService> objekt v metodě ve třídě.

 V <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> implementaci metody, pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> je vlastnost `true`nastavena na <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> , můžete vrátit objekt. Pokud objekt nevrátíte, navigační panel se nezobrazí.

 Možnost zobrazit navigační panel může být nastavena uživatelem, takže je možné, aby tento ovládací prvek resetovat, zatímco zobrazení editoru je otevřen. Uživatel musí zavřít a znovu otevřít okno editoru před změnou probíhá.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementace podpory navigačního panelu
 Metoda <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> trvá dva seznamy (jeden pro každý rozevírací seznam) a dvě hodnoty představující aktuální výběr v každém seznamu. Seznamy a hodnoty výběru lze aktualizovat, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> v `true` takovém případě se musí metoda vrátit, aby bylo zřejmé, že seznamy byly změněny.

 Při změnách výběru v rozevíracím seznamu typů musí být seznam členů aktualizován tak, aby odrážel nový typ. Co je zobrazeno v seznamu členů může být buď:

- Seznam členů pro aktuální typ.

- Všechny členy dostupné ve zdrojovém souboru, ale se všemi členy, které nejsou v aktuálním typu zobrazeny šedě. Uživatel může stále vybrat šedě zobrazené členy, takže je lze použít pro rychlou navigaci, ale barva označuje, že nejsou součástí aktuálně vybraného typu.

  Implementace <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metody obvykle provádí následující kroky:

1. Získejte seznam aktuálních deklarací zdrojového souboru.

     Seznamy mohou naplnit několika způsoby. Jedním z přístupů je vytvořit vlastní <xref:Microsoft.VisualStudio.Package.LanguageService> metodu ve <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> vaší verzi třídy, která volá metodu s vlastní analýzy důvod, který vrací seznam všech deklarací. Jiný přístup může být <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> volání metody <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> přímo z metody s vlastní analýzy důvodu. Třetí přístup může být do mezipaměti <xref:Microsoft.VisualStudio.Package.AuthoringScope> deklarace ve třídě vrácené poslední <xref:Microsoft.VisualStudio.Package.LanguageService> úplné analýzy <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> operace ve třídě a načíst z metody.

2. Naplnit nebo aktualizovat seznam typů.

     Obsah seznamu typů může být aktualizován, pokud se zdroj změnil nebo pokud jste se rozhodli změnit styl textu typů na základě aktuální polohy stříšky. Všimněte si, že <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> tato pozice je předána metodě.

3. Určete typ, který chcete vybrat v seznamu typů na základě aktuální polohy stříšky.

     Můžete prohledat deklarace, které byly získány v kroku 1 najít typ, který obklopuje aktuální pozici stříšky a potom prohledejte seznam typů pro tento typ k určení jeho indexu do seznamu typů.

4. Naplňte nebo aktualizujte seznam členů na základě vybraného typu.

     Seznam členů odráží to, co je aktuálně zobrazeno v rozevíracím seznamu **Členové.** Obsah seznamu členů může být nutné aktualizovat, pokud se zdroj změnil nebo pokud zobrazujete pouze členy vybraného typu a vybraný typ byl změněn. Pokud se rozhodnete zobrazit všechny členy ve zdrojovém souboru, je třeba aktualizovat textový styl každého člena v seznamu, pokud se aktuálně vybraný typ změnil.

5. Určete člena, který chcete vybrat v seznamu členů na základě aktuální pozice stříšky.

     Hledat deklarace, které byly získány v kroku 1 pro člena, který obsahuje aktuální pozici stříšky, pak hledání seznamu členů pro tento člen určit jeho index do seznamu členů.

6. Vraťte `true` se, pokud byly provedeny nějaké změny v seznamech nebo výběrech v obou seznamech.
