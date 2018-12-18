---
title: 'Postupy: vytvoření typu s možnou hodnotou Null (návrhář tříd) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab5bfe3068f79bceb02352b47de4beb08da75c85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941942"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Postupy: Vytváření typů s povolenou hodnotou Null (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé typy hodnot ne vždy mají (nebo potřebujete) definovanou hodnotu. To je běžný postup v databázích, ve kterém některá pole nemůže být přiřazen žádnou hodnotu. Můžete například přiřadit hodnotu null do pole databáze místo, že ho nebyl dosud byla přiřazena hodnota.  
  
 A *typ připouštějící hodnotu Null* je hodnotový typ, který jste rozšířit tak, aby trvá Typická rozsah hodnot pro daný typ a také hodnotu null. Například s povolenou hodnotou NULL z `Int32`, také označeny jako s možnou hodnotou Null\<Int32 >, je možné přiřadit libovolnou hodnotu od -2147483648 do 2147483647 nebo je možné přiřadit hodnotu null. Nullable\<bool > je možné přiřadit hodnoty `True`, `False`, nebo hodnota null (žádná hodnota vůbec).  
  
 Typy s možnou hodnotou Null jsou instance <xref:System.Nullable%601> struktury. Každá instance typu s možnou hodnotou Null má dvě veřejné vlastnosti jen pro čtení `HasValue` a `Value`:  
  
- `HasValue` je typu `bool` a určuje, zda je proměnná obsahuje definovanou hodnotu. `True` znamená to, že proměnná obsahuje hodnotu než null. Můžete otestovat pomocí příkazu pro definovanou hodnotou `if (x.HasValue)` nebo `if (y != null)`.  
  
- `Value` je stejného typu jako základní typ. Pokud `HasValue` je `True`, `Value` obsahuje smysluplnou hodnotu. Pokud `HasValue` je `False`, přístup k `Value` vyvolá výjimku neplatná operace.  
  
  Ve výchozím nastavení, pokud deklarujete proměnnou jako typ s možnou hodnotou Null nemá žádné definované hodnoty (`HasValue` je `False`), jiné než výchozí hodnotu jeho základní typ hodnoty.  
  
  Návrhář tříd zobrazí typ připouštějící hodnotu Null, stejně jako zobrazí jeho nadřízeného typu.  
  
  Další informace o typech s povolenou hodnotou Null v jazyce Visual C# najdete v tématu [typy připouštějící hodnotu Null](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Další informace o typech s povolenou hodnotou Null v jazyce Visual Basic najdete v tématu [hodnotové typy s možnou hodnotou Null](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Chcete-li přidat typ připouštějící hodnotu Null pomocí návrháře tříd  
  
1.  V diagramu tříd rozšiřte existující třídy nebo vytvořte novou třídu.  
  
2.  Přidání třídy do projektu, na **Diagram tříd** nabídky, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.  
  
3.  Rozbalte obrazec třídy na **Diagram tříd** nabídky, klikněte na tlačítko **Rozbalit**.  
  
4.  Vyberte obrazec třídy. Na **Diagram tříd** nabídky, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **pole**. Nové pole, která má výchozí název **pole** se zobrazí na obrazec třídy a také **podrobností třídy** okna.  
  
5.  V **název** sloupec **podrobností třídy** okna (nebo ve třídě obrazce samotné), změňte název nového pole na platný a smysluplný název.  
  
6.  V **typ** sloupec **podrobností třídy** okna, deklarujte typ jako typ s možnou hodnotou Null, jak je znázorněno v následujícím kódu:  
  
    ```csharp  
    // Declare a nullable type in Visual C#:  
    class Test  
    {  
       int? building_number = 5;  
    }  
    ```  
  
    ```vb  
    ' Declare a nullable type in Visual Basic:  
    Class Test  
       Dim buildingNumber As Nullable(Of Integer) = 5  
    End Class  
    ```  
  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Chcete-li přidat typ připouštějící hodnotu Null pomocí editoru kódu  
  
1.  Přidání třídy do projektu. Vyberte uzel projektu v **Průzkumníku řešení**a dále **projektu** nabídky, klikněte na tlačítko **přidat třídu**.  
  
2.  V souboru .cs nebo .vb pro novou třídu přidejte jeden nebo více typů s povolenou hodnotou Null v této nové třídě do deklarace třídy.  
  
3.  Ze zobrazení tříd přetáhněte přes novou ikonu třídy na návrhové ploše návrháře tříd. Tvar třídy se zobrazí v diagramu tříd.  
  
4.  Rozbalit podrobnosti pro třídu tvar a přesuňte ukazatel myši nad členy třídy. Popisek zobrazí deklarace každého člena.  
  
5.  Pravým tlačítkem myši na obrazec třídy a klikněte na tlačítko **podrobností třídy**. Můžete zobrazit nebo upravit vlastnosti nového typu **podrobností třídy** okna.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Nullable%601>   
 [Typy s možnou hodnotou Null](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)   
 [Použití typů s povolenou hodnotou Null](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)   
 [Postupy: identifikace typu s možnou hodnotou Null](http://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)   
 [Typy hodnot s povolenou hodnotou Null](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)



