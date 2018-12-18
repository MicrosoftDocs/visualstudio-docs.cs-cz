---
title: 'Postupy: přidávání ověřování do tříd entit | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91600821b3d68c04382028e469a4e1a54a5d191c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812746"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Postupy: přidávání ověřování do tříd entit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
*Ověřování* tříd entit je proces ověření, že hodnoty zadané do datových objektů v souladu s omezeními ve schématu objektu a také pravidel stanovených pro aplikaci. Ověřování dat před odesláním aktualizace do podkladové databáze je dobrým zvykem, která snižuje chyby. Také snižuje potenciální počet výměn mezi aplikací a databáze.  
  
 [LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytuje částečným metodám, které uživatelům umožňují rozšířit kód generovaný návrhářem, který spustí během vložení, aktualizace a odstranění kompletní entit a také během a po jednotlivých sloupců změny.  
  
> [!NOTE]
>  Toto téma popisuje základní kroky pro přidání ověřování do tříd entit pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Vzhledem k tomu může být obtížné postupovat podle následujících obecných kroků bez ohledu na konkrétní entitu třídu, byl poskytnut návod, který používá skutečná data.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Přidání ověřování pro změny s hodnotou v určitém sloupci  
 Tento postup ukazuje, jak ověřit data při změně hodnoty ve sloupci. Protože ověření se provede uvnitř definice třídy (místo v uživatelském rozhraní) je vyvolána výjimka, pokud hodnota způsobí selhání ověření. Implementace zpracování chyb pro kód ve vaší aplikaci, která se pokusí změnit hodnoty ve sloupcích.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>Ověření dat při změně hodnoty sloupce.  
  
1. Otevřete nebo vytvořte novou LINQ na třídy SQL soubor (**dbml** souborů) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Dvakrát klikněte **dbml** ve **Průzkumníka řešení**.)  
  
2. V Návrháři relací objektů klikněte pravým tlačítkem na třídu, pro který chcete přidat ověřování a pak klikněte na tlačítko **zobrazit kód**.  
  
    Otevře se Editor kódu s částečnou třídu pro třídy vybranou entitu.  
  
3. Umístěte kurzor do částečné třídy.  
  
4. Pro projekty jazyka Visual Basic:  
  
   1. Rozbalte **název metody** seznamu.  
  
   2. Vyhledejte **na**_NÁZEVSLOUPCE_**změna** metodu pro sloupec, který chcete přidat k ověření.  
  
   3. `On` *NÁZEVSLOUPCE* `Changing` metoda je přidána do částečné třídy.  
  
   4. Přidejte následující kód, který nejprve ověřte, zda byla zadána hodnota, a pak zajistit, aby hodnota zadaná pro sloupec je přijatelné pro vaši aplikaci. `value` Argument obsahuje navrhovanou hodnotu, takže přidání logiky pro potvrzení, že se jedná o platnou hodnotu:  
  
      ```vb  
      If value.HasValue Then  
          ' Add code to ensure that the value is acceptable.  
          ' If value < 1 Then  
          '    Throw New Exception("Invalid data!")  
          ' End If  
      End If  
      ```  
  
      Pro projekty jazyka C#:  
  
   5. Protože projekty jazyka C# negenerují automaticky obslužné rutiny událostí, můžete vytvořit částečné metody se měnící sloupec technologie IntelliSense.  
  
       Typ `partial` a pak prostor pro přístup k seznamu k dispozici částečné metody. Klikněte na metodu se měnících sloupce pro sloupec, který chcete přidat ověřování. Následující kód se podobá kód, který se vygeneruje, když vyberete částečné metody se měnící sloupec:  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Přidání ověřování pro aktualizace pro třídu Entity  
 Kromě kontroly toho hodnoty během změny, můžete také ověřit data při pokusu o aktualizaci třídu úplnou entitu. Ověření během pokusu o aktualizaci můžete porovnat hodnoty ve více sloupcích, pokud to vyžadují obchodní pravidla. Následující postup ukazuje, jak ověřit při pokusu o aktualizaci třídu úplnou entitu.  
  
> [!NOTE]
>  Ověřovací kód pro aktualizace dokončete tříd entit je proveden v částečnou <xref:System.Data.Linq.DataContext> třídy (místo v dílčí třídě konkrétní entity třídy).  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Ověření dat během aktualizace do třídy entity  
  
1. Otevřete nebo vytvořte novou LINQ na třídy SQL soubor (**dbml** souborů) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Dvakrát klikněte **dbml** ve **Průzkumníka řešení**.)  
  
2. Klikněte pravým tlačítkem myši na prázdnou oblast Návrháře relací objektů a klikněte na tlačítko **zobrazit kód**.  
  
    Otevře se Editor kódu s částečnou třídu `DataContext`.  
  
3. Umístěte kurzor do částečné třídy pro `DataContext`.  
  
4. Pro projekty jazyka Visual Basic:  
  
   1. Rozbalte **název metody** seznamu.  
  
   2. Klikněte na tlačítko **aktualizace**_ENTITYCLASSNAME_.  
  
   3. `Update` *ENTITYCLASSNAME* metoda je přidána do částečné třídy.  
  
   4. Přístup s použitím hodnot jednotlivých sloupců `instance` argument, jak je znázorněno v následujícím kódu:  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      Pro projekty jazyka C#:  
  
   5. Protože projekty jazyka C# negenerují automaticky obslužné rutiny událostí, technologie IntelliSense můžete použít k vytvoření částečnou `Update` *CLASSNAME* metody.  
  
   6. Typ `partial` a pak prostor pro přístup k seznamu k dispozici částečné metody. Klikněte na metodu aktualizace pro třídu, kterou chcete přidat ověřování. Následující kód se podobá kód, který se vygeneruje, když vyberete `Update` *CLASSNAME* částečné metody:  
  
      ```csharp  
      partial void UpdateCLASSNAME(CLASSNAME instance)  
      {  
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
          {  
              string ErrorMessage = "Invalid data!";  
              throw new System.Exception(ErrorMessage);  
          }  
      }  
      ```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)

