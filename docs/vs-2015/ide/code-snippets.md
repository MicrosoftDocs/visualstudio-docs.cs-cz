---
title: Fragmenty kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b41b6e4d4a7635b32edb5697c89ecb1249fb9da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619731"
---
# <a name="code-snippets"></a>Fragmenty kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu jsou malé bloky opakovaně použitelného kódu, který lze vložit do souboru kódu pomocí příkazu místní nabídky nebo kombinace klávesových zkratek. Obvykle obsahují často používané bloky kódu, jako jsou například try-finally nebo if-else, ale lze je použít k vložení celé třídy nebo metod.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty rozšíření a obklopení s fragmenty
 V aplikaci Visual Studio existují dva druhy fragmentů kódu: fragmenty rozšíření, které jsou přidány v zadaném místě vložení a mohou nahradit zástupce fragmentu a obklopit pomocí fragmentů (pouze C# a C++), které jsou přidány kolem vybraného bloku kódu.

 Příklad fragmentu vložení: v jazyce C# je pro vložení bloku try-finally použit zástupce tryf:

```
try
{

}
finally
{

}

```

 Tento fragment kódu můžete vložit kliknutím na **Vložit fragment** v kontextové nabídce okna kód, potom v **jazyce Visual C#**, zadáním `tryf` , tabulátoru nebo můžete zadat `tryf` a stisknout tabulátor + TAB.

 Příklad obklopit s fragmentem kódu: v jazyce C++ zástupce `if` lze použít buď jako fragment vložení, nebo jako obklopit s fragmentem kódu. Pokud vyberete řádek kódu (například `return FALSE;` ) a pak kliknete na možnost **obklopit s**, pak **if**se fragment kódu rozbalí kolem řádku:

```
if (true)
{
    return FALSE;
}

```

## <a name="snippet-replacement-parameters"></a>Parametry nahrazení fragmentů
 Fragmenty kódu mohou obsahovat náhradní parametry, což jsou zástupné symboly, které je nutné nahradit, aby odpovídaly přesnému kódu, který píšete. V předchozím příkladu `true` je náhradní parametr, který byste nahradili příslušnou podmínkou. Náhrada, kterou provedete, se opakuje pro každou instanci stejného parametru nahrazení ve fragmentu.

 Například v Visual Basic existuje fragment kódu, který vloží vlastnost. V kontextové nabídce okna kódu klikněte na **Vložit fragment** **kódu, pak na** **vlastnosti, procedury, události**a pak na definovat vlastnost. Je vložen následující kód:

```
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property

```

 Změníte-li `newPropertyValue` na `m_property` , pak dojde ke změně každé instance `newPropertyValue` . Pokud se `String` `Int` v deklaraci vlastnosti změní na, pak je hodnota v metodě set také změněna na `Int` .

## <a name="code-snippet-manager"></a>Správce fragmentů kódu
 Kliknutím na tlačítko **nástroje/Správce fragmentů kódu**uvidíte všechny aktuálně nainstalované fragmenty kódu a jejich umístění na disku. Fragmenty kódu se zobrazují podle jazyka.

 Můžete přidávat a odebírat fragmenty adresářů pomocí tlačítek **Přidat** a **Odebrat** v dialogovém okně **Správce fragmentů kódů** . Chcete-li přidat jednotlivé fragmenty kódu, použijte tlačítko **Import** .

## <a name="see-also"></a>Viz také
 [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md) [Postupy: distribuce](../ide/how-to-distribute-code-snippets.md) [kódu osvědčené postupy pro používání fragmentů](../ide/best-practices-for-using-code-snippets.md) kódu [řešení potíží s](../ide/troubleshooting-snippets.md) fragmenty kódu [jazyka Visual C#](../ide/visual-csharp-code-snippets.md) [Visual C++](../ide/visual-cpp-code-snippets.md) [odkaz na schéma](../ide/code-snippets-schema-reference.md) fragmentů kódu v jazyce Visual C#
