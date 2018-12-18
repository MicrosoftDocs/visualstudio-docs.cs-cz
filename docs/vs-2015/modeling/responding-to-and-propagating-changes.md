---
title: Reagování na změny a šíření změn | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 32deaa75ed09ad1a1320ec72d95d75adc92c12b2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280381"
---
# <a name="responding-to-and-propagating-changes"></a>Reagování na změny a šíření změn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po elementu se vytvoří, odstraní nebo aktualizuje, můžete napsat kód, který šíří změny dalších součástí modelu, nebo k externím prostředkům, jako jsou soubory, databáze nebo další komponenty.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Jako vodítko vezměte v úvahu tyto postupy v tomto pořadí:  
  
|Postup|Scénáře|Další informace|  
|---------------|---------------|--------------------------|  
|Definujte počítané doménové vlastnosti.|Doménová vlastnost, jejíž hodnota se počítá od jiné vlastnosti v modelu. Například cena, která je součtem ceny souvisejících prvků.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|  
|Definujte doménová vlastnost, která vlastní úložiště.|Doménová vlastnost, která uložena v ostatních částech modelu nebo externě. Například může analyzovat řetězec výraz do stromu v modelu.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|  
|Přepsání změnit obslužné rutiny, například OnValueChanging a OnDeleting|Udržovat synchronizované různé prvky a udržovat synchronizované s modelem externí hodnoty.<br /><br /> Omezení hodnoty, které mají definovanou oblastí.<br /><br /> Volá se bezprostředně před a po hodnotě vlastnosti a jiné změny. Tato změna může ukončit vyvoláním výjimky.|[Obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md)|  
|pravidla|Můžete definovat pravidla, které jsou zařazeny do fronty pro provedení pouze do konce transakce, ve které došlo ke změně. Nejsou provedeny na vrácení zpět nebo znovu. Jejich použití jedné části úložiště synchronizace s jinou.|[Pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md)|  
|Store události|Modelování úložiště poskytuje oznámení o události, například přidávání nebo odstraňování elementu nebo propojení nebo změna hodnoty vlastnosti. Událost je také provést na zpět a znovu. Události v úložišti slouží k aktualizaci hodnoty, které nejsou v úložišti.|[Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Události .NET|Obrazce mají obslužné rutiny událostí, které reagují na kliknutí myší a dalších gesta. Je nutné provést registraci pro tyto události pro každý objekt. Registrace se obvykle provádí v přepsání InitializeInstanceResources a je nutné provést pro každý prvek.<br /><br /> Tyto události obvykle dochází mimo transakci.|[Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Rozsah pravidla|Hranice pravidlo se používá konkrétně, chcete-li omezit rozsah tvaru.|[Umístění a velikost obrazce omezení BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Výběr pravidla|Výběr pravidla konkrétně omezit, co může uživatel vybrat.|[Postupy: Přístup k aktuálnímu výběru a jeho omezení](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Označuje nové elementy modelu pomocí funkce obrazců a konektorů, jako jsou stínové, šipky, barvy a šířku čáry a stylu.|[Aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Porovnání pravidla a Store události**  
 Změna žadateli, pravidla a události se spouštějí při změnách v modelu.  
  
 Pravidla se obvykle používají v celé transakci, ve kterém došlo k změny a události se použijí po potvrzení změn v rámci transakce.  
  
 Při události v úložišti se budou synchronizovat model s objekty mimo Store a pravidla můžete zachovat konzistenci v rámci Store.  
  
-   **Vytváření vlastních pravidel** jako odvozené třídy abstraktní pravidlo vytvoříte vlastní pravidlo. Musíte také upozornit framework o vlastní pravidlo. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Přihlášení k odběru událostí** předtím, než se můžete přihlásit odběr události, vytvořit obslužnou rutinu události a delegáta. Potom použijte <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>vlastnost k odběru události. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Ruší se provedené změny** při vrácení transakce, jsou vyvolány události, ale pravidla se nepoužijí. Pokud pravidlo změní hodnotu a můžete tuto změnu vrátit zpět, je hodnota obnovit během akce vrátit zpět na původní hodnotu. Když je vyvolána událost, musíte ručně změnit hodnotu zpět na původní hodnotu. Další informace o transactons a vrácení zpět, najdete v článku [postupy: používání transakcí k aktualizaci modelu](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Předávání argumentů událostí k pravidla a akce** obou událostí a pravidla jsou předány `EventArgs` parametr, který obsahuje informace o tom, model změnit.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zachycení kliknutí na obrazec či Dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)



