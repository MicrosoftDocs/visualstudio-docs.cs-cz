---
title: 'Postupy: implementace operace Windows Communication Foundation kontraktu (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603868"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Postupy: implementace operace Windows Communication Foundation kontraktu (starší verze)
Toto téma popisuje, jak implementovat operaci [!INCLUDE[indigo1](../includes/indigo1-md.md)] kontraktu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)], která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Po přetažení aktivity **ReceiveActivity** ze sady nástrojů na návrhovou plochu pracovního postupu vytvoříte novou [!INCLUDE[indigo2](../includes/indigo2-md.md)] smlouvu nebo naimportujete stávající kontrakt a implementujete operace. Můžete vybrat nebo vytvořit svůj kontrakt a jeho operace pomocí [dialogového okna zvolit operaci (starší verze)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Implementace operace kontraktu WCF

1. Dvakrát klikněte na aktivitu **ReceiveActivity** v Návrháři nebo klikněte na tři tečky vedle vlastnosti **ServiceOperationInfo** v podokně **vlastnosti** .

2. Proveďte jednu z těchto akcí:

   - Klikněte na **Přidat kontrakt** v pravém horním rohu dialogového okna. Tím se vytvoří nový kontrakt [!INCLUDE[indigo2](../includes/indigo2-md.md)] a operace za vás.

      -nebo-

   - V pravém horním rohu dialogového okna klikněte na **importovat** . Otevře se [dialogové okno Procházet a vybrat typ .NET (starší verze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) . Vyhledejte sestavení nebo projekt, které obsahují kontrakt, který chcete. Vyberte kontrakt a klikněte na **OK**.

     Po vytvoření nebo importu smlouvy můžete přidat nové operace do tohoto vytvořeného nebo importovaného kontraktu. Chcete-li přidat novou operaci, vyberte kontrakt a klikněte na tlačítko **přidat operaci** v pravém horním rohu dialogového okna. Až skončíte s přidáváním operací, pokračujte krokem 3.

3. Vyberte operaci, kterou chcete přidružit k aktivitě **ReceiveActivity** . Můžete manipulovat s definicí operace změnou názvu, parametrů, vlastností a nastavení oprávnění operace.

    Chcete-li změnit název, zadejte nový název do textového pole **název operace** .

    Kliknutím na kartu **parametry** získáte přístup k parametrům operace. Můžete změnit název, typ nebo směr parametru a také přidat nebo odstranit parametry z operace.

    Kliknutím na kartu **vlastnosti** získáte přístup k úrovni ochrany operace a podporované funkci výměny zpráv.

    Klikněte na kartu **oprávnění** a určete, které skupiny mají povoleno implementaci operace.

4. Klikněte na **OK** a aktivita **ReceiveActivity** zobrazí název operace pro operaci, kterou implementuje.

5. Umístěte aktivity pracovního postupu, které budete používat pro implementaci této operace v rámci aktivity **ReceiveActivity** .

## <a name="see-also"></a>Viz také
 [Výběr operace – dialogové okno (starší verze)](../workflow-designer/choose-operation-dialog-box-legacy.md) [Postupy: vyvolání operace kontraktu WCF (starší verze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [starší aktivity pracovního postupu](../workflow-designer/legacy-workflow-activities.md)