---
title: Refaktoring (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667504"
---
# <a name="refactoring-c"></a>Refaktoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoring je proces vylepšení kódu po jeho zapsání změnou vnitřní struktury kódu beze změny externího chování kódu.

 Vizuál C# poskytuje následující příkazy refaktoringu v nabídce **refaktoringu** :

- [Refaktoring pro extrahování metody (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refaktoring pro přejmenování (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Refaktoring pro zapouzdření polí (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refaktoring pro extrahování rozhraní (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Refaktoring pro odebrání parametrů (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Refaktoring pro přeskupení parametrů (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refaktoring více projektů
 Visual Studio podporuje refaktoring více projektů pro projekty, které jsou ve stejném řešení. Všechny operace refaktoringu, které správně odkazují na soubory, opravují odkazy napříč všemi projekty stejného jazyka. To funguje pro všechny odkazy mezi projekty. Například pokud máte konzolovou aplikaci, která odkazuje na knihovnu tříd, při přejmenování typu knihovny tříd (pomocí operace refaktoringu `Rename`) jsou aktualizovány také odkazy na typ knihovny tříd v konzolové aplikaci.

## <a name="changes-preview"></a>Změny ve verzi Preview
 Mnohé operace refaktoringu poskytují příležitost pro kontrolu všech změn odkazů, které by u vašeho kódu prováděla operace refaktoringu, a to před potvrzením změn. V případě těchto operací refaktoringu se v dialogovém okně refaktoringu zobrazí možnost **Náhled změn odkazu** . Po výběru této možnosti a přijetí operace refaktoringu se zobrazí **dialogové okno Náhled změn** . Všimněte si, že dialogové okno **Náhled změn** má dvě zobrazení. V dolním zobrazení se v důsledku operace refaktoringu zobrazí váš kód se všemi referenčními aktualizacemi. Kliknutím na **tlačítko Storno** v dialogovém okně **Náhled změn** dojde k zastavení operace refaktoringu a v kódu nebudou provedeny žádné změny.

## <a name="refactoring-warnings"></a>Upozornění refaktoringu
 Pokud kompilátor nemá úplný princip programu a je možné, že modul refaktoringu nemusí aktualizovat všechny příslušné odkazy, zobrazí se dialogové okno upozornění. Toto dialogové okno s upozorněním vám také nabídne možnost zobrazit náhled kódu v dialogovém okně **Náhled změn** před potvrzením změn.

> [!NOTE]
> Pokud metoda obsahuje syntaktickou chybu (která IDE indikuje červené vlnovkou), pak modul refaktoringu nebude aktualizovat žádné odkazy na element v rámci této metody. Následující příklad znázorňuje toto chování.

 Ve výchozím nastavení platí, že pokud provádíte operaci refaktoringu bez náhledu změn odkazů a v programu je zjištěna chyba kompilace, pak vývojové prostředí zobrazí toto dialogové okno s upozorněním.

 Pokud provedete operaci refaktoringu, která má zapnuté **změny odkazu Preview** a v programu se zjistí chyba kompilace, ve vývojovém prostředí se v dolní části náhledu zobrazí následující zpráva s upozorněním.místo zobrazení dialogového okna pro **Upozornění refaktoringu** , a to v dialogovém okně:

 **Váš projekt nebo jedna z jeho závislostí není aktuálně sestavena. Odkazy nelze aktualizovat.**

 Toto upozornění refaktoringu je k dispozici pouze pro operace refaktoringu, které poskytují možnost **Náhled změn odkazů** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Refaktoring a výsledky ověřování odolné vůči chybám
 Refaktoring je odolný vůči chybám. Jinými slovy, můžete provést Refaktoring v projektu, který nelze sestavit. V těchto případech však proces refaktoringu nemusí správně aktualizovat nejednoznačné odkazy.

 V dialogovém okně **výsledky ověření** se může zobrazit výzva, pokud modul refaktoringu detekuje chyby kompilace nebo zjistí, že operace refaktoringu neúmyslně způsobí, že se odkaz na kód sváže s jiným objektem, který byl původně svázán ( problém s opětovnou vazbou).

 Chcete-li zapnout funkci výsledky ověřování, v nabídce **nástroje** klikněte na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte položku **textový editor**a poté rozbalte položku. **C#** Klikněte na tlačítko **Upřesnit** a zaškrtněte políčko **ověřit výsledky refaktoringu** .

 Dialogové okno **výsledky ověření** rozlišuje rozdíl mezi dvěma druhy revázání problémů.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Odkazy, jejichž definice již nebude přejmenován na symbol
 Tento druh problému s opětovnou vazbou nastane, když odkaz už neodkazuje na přejmenovaný symbol. Zvažte například následující kód:

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 Použijete-li refaktoring k přejmenování `a` na `b`, zobrazí se toto dialogové okno. Odkaz na přejmenovanou proměnnou `a` nyní váže k parametru, který je předán konstruktoru namísto vazby k poli.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Odkazy, jejichž definice se nyní změní na přejmenovaný symbol
 Tento druh potíží s opětovnou vazbou nastane, pokud odkaz, který dříve neodkazoval na přejmenovaný symbol, teď odkazuje na přejmenovaný symbol. Zvažte například následující kód:

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 Použijete-li refaktoring k přejmenování `OtherMethod` na `Method`, zobrazí se toto dialogové okno. Odkaz v `Main` nyní odkazuje na přetíženou metodu, která přijímá parametr `int` namísto přetížené metody, která přijímá parametr `object`.

## <a name="see-also"></a>Viz také
 [Použití vývojového prostředí sady Visual Studio C# pro](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [Postupy: obnovení C# fragmentů refaktoringu](../ide/how-to-restore-csharp-refactoring-snippets.md)