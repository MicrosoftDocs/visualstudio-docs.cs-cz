---
title: 'Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic) | Dokumentace Microsoftu'
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
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 730ebcf8029abf51e6cb04c74b826593139cfdc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196395"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Import oboru názvů umožňuje použít elementy z daného oboru názvů ve vašem kódu bez plně kvalifikovaného elementu. Například, pokud chcete získat přístup `Create` metoda ve `System.Messaging.MessageQueue` třídy, můžete importovat `System.Messaging` obor názvů a stačí odkazovat na prvek, je nutné v kódu jako `MessageQueue.Create`.  
  
 Importované obory názvů jsou spravovány v **odkazy** stránku **Návrháře projektu**. Importy, které zadáte v tomto dialogovém jsou předány přímo kompilátor (`/imports`) a použít na všechny soubory ve vašem projektu. Použít `Imports` příkaz pro použití oboru názvů v jediném souboru kódu.  
  
### <a name="to-add-an-imported-namespace"></a>Přidání importované oboru názvů  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte **Můj projekt** uzel projektu.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **odkazy** kartu.  
  
3.  V **importované obory názvů** seznam, zaškrtněte políčko pro obor názvů, který chcete přidat.  
  
    > [!NOTE]
    >  Aby bylo možné importovat, musí být obor názvů v odkazované součásti. Pokud obor názvů se nezobrazí v seznamu, musíte přidat odkaz na komponentu, která ji obsahuje. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### <a name="to-remove-an-imported-namespace"></a>Chcete-li odebrat importované oboru názvů  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte **Můj projekt** uzel projektu.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **odkazy** kartu.  
  
3.  V **importované obory názvů** seznamu, zrušte zaškrtnutí políčka pro obor názvů, který chcete odebrat.  
  
## <a name="user-imports"></a>Importy uživatele  
 Importy uživatele bylo možné importovat konkrétní třídu v rámci oboru názvů, ne celý obor názvů. Například aplikace může mít import `Systems.Diagnostics` je obor názvů, ale pouze třídy v daném oboru názvů, které vás zajímají `Debug` třídy. Můžete definovat `System.Diagnostics.Debug` jako uživatel importovat a pak odeberte import pro `System.Diagnostics`.  
  
 Pokud později změníte názor a rozhodnout, který se ve skutečnosti na `EventLog` třídy, které jsme potřebovali, můžete například zadat `System.Diagnostics.EventLog` jako uživatel, importovat a přepsat `System.Diagnostics.Debug` pomocí funkce aktualizace.  
  
#### <a name="to-add-a-user-import"></a>Chcete-li přidat import uživatelů  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte **Můj projekt** uzel projektu.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **odkazy** kartu.  
  
3.  Do textového pole níže **importované obory názvů** seznamu, zadejte úplný název pro obor názvů, který chcete importovat, včetně kořenový obor názvů.  
  
4.  Klikněte na tlačítko **přidat import uživatelů** tlačítko pro přidání oboru názvů **importované obory názvů** seznamu.  
  
    > [!NOTE]
    >  **Přidat import uživatelů** tlačítko bude zakázáno, pokud obor názvů odpovídá jednomu již v seznamu; nelze přidat import dvakrát.  
  
#### <a name="to-update-a-user-import"></a>Chcete-li aktualizovat import uživatelů  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte **Můj projekt** uzel projektu.  
  
2.  V **Návrháře projektu**, klikněte na tlačítko **odkazy** kartu.  
  
3.  V **importované obory názvů** vyberte obor názvů, který chcete změnit.  
  
4.  Do textového pole níže **importované obory názvů** seznamu, zadejte název pro nový obor názvů.  
  
5.  Klikněte na tlačítko **aktualizovat import uživatelů** tlačítko Aktualizovat v oboru názvů **importované obory názvů** seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)



