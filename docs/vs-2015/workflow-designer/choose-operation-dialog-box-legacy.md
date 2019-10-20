---
title: Dialogové okno zvolit operaci (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659165"
---
# <a name="choose-operation-dialog-box-legacy"></a>Dialogové okno Zvolit operaci (starší verze)
Toto téma popisuje, jak použít dialogové okno **Vybrat operaci** ve starší verzi [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] použijte, pokud potřebujete cílit buď na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)], nebo na [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dialogové okno **Zvolit operaci** slouží k výběru operace, která se má přidružit k aktivitě <xref:System.Workflow.Activities.ReceiveActivity> nebo aktivitě <xref:System.Workflow.Activities.SendActivity>. Další informace o použití tohoto dialogového okna spolu s těmito aktivitami naleznete v tématu [How to: Implement a Operations kontrakt WCF (starší verze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) a [How to: Invoke Operations kontraktu WCF (starší verze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) dialogového okna **Zvolit operaci** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Přidat kontrakt**|Vytvoří novou smlouvu za vás. U této smlouvy můžete definovat nové operace. (Používá se jenom pro <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Přidat operaci**|Přidá nové operace do nového kontraktu, který jste vytvořili v dialogovém okně **Vybrat operaci** . **Poznámka:**  Nové operace můžete přidat pouze ke smlouvám, které jste vytvořili v dialogovém okně **Vybrat operaci** . <br /><br /> (Používá se jenom pro <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Importovat...**|Importuje dříve definovaný kontrakt a umožňuje vybrat operaci z této smlouvy.|
|**Název operace**|Název aktuálně vybrané operace. Toto textové pole je k dispozici pro úpravy pouze v případě, že jste vytvořili operaci pomocí dialogového okna **Zvolit operaci** .|
|**Parametry**|Karta obsahující definice parametrů pro aktuálně vybranou operaci **Poznámka:**  Definice parametrů lze změnit pouze v případě, že jste vytvořili operaci pomocí dialogového okna **Zvolit operaci** .|
|**Vlastnosti**|Karta obsahující nastavení <xref:System.Net.Security.ProtectionLevel> pro zprávy odesílané mezi klientem a službou. **Poznámka:**  Tato karta je povolena pouze v případě, že jste vytvořili operaci pomocí dialogového okna **Zvolit operaci** .|
|**Oprávnění**|Karta obsahující <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> a <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> vlastnosti uživatelů, kterým je povolena volání této operace. Například pokud bylo povoleno volání této operace pouze uživatelům ze skupiny Administrators, pak do textového pole **role** zapíšete "Administrators".<br /><br /> Tato karta je povolena pro obě operace vytvořené prostřednictvím dialogového okna **ChooseOperation** a operace, které byly importovány prostřednictvím tlačítka **Import** .|

> [!NOTE]
> Dialogové okno **Zvolit operaci** zobrazuje jenom kontrakty nebo operace, které používají jiné aktivity <xref:System.Workflow.Activities.SendActivity> v pracovním postupu. Podobně dialog **Vybrat operaci** pro aktivity <xref:System.Workflow.Activities.ReceiveActivity> zobrazuje pouze kontrakty nebo operace, které používají jiné aktivity **ReceiveActivity** v pracovním postupu.

## <a name="see-also"></a>Viz také
 [Postupy: implementace operace kontraktu WCF (starší verze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [Postupy: vyvolání operace kontraktu WCF (starší verze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Návrhář starší verze pro programovací model Windows Workflow Foundation nápovědu k uživatelskému rozhraní](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)