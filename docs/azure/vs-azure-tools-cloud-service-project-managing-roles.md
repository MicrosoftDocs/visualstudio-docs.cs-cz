---
title: Správa rolí v cloudových službách Azure
description: Přečtěte si, jak přidávat a odebírat role v cloudových službách Azure pomocí Visual Studia.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: f03ac134a54f3a32108175fa858d22b5c4aec8af
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489685"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Správa rolí v cloudových službách Azure pomocí Visual Studia
Po vytvoření cloudové služby Azure do ní můžete přidat nové role nebo z ní odebrat existující role. Můžete také importovat existující projekt a převést jej na roli. Můžete například importovat ASP.NET webovou aplikaci a označit ji jako webovou roli.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Přidání role do cloudové služby Azure
Následující kroky vás provedou přidáním role webu nebo pracovního procesu do projektu cloudové služby Azure ve Visual Studiu.

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu.

1. Chcete-li zobrazit místní nabídku, klepněte pravým tlačítkem myši na uzel **Role.** V místní nabídce vyberte **Přidat**, vyberte existující webovou roli nebo roli pracovního procesu z aktuálního řešení nebo vytvořte projekt webových nebo pracovních rolí. Můžete také vybrat vhodný projekt, například projekt webové aplikace ASP.NET, a přidružit jej k projektu role.

   ![Možnosti nabídky pro přidání role do projektu cloudové služby Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Odebrání role z cloudové služby Azure
Následující kroky vás provedou odebráním webové nebo pracovní role z projektu cloudové služby Azure v sadě Visual Studio.

1. Vytvořte nebo otevřete projekt cloudové služby Azure ve Visual Studiu.

1. V **Průzkumníku řešení**rozbalte uzel projektu.

1. Rozbalte uzel **Role.**

1. Klikněte pravým tlačítkem myši na uzel, který chcete odebrat, a v místní nabídce vyberte **Odebrat**.

   ![Možnosti nabídky pro přidání role do cloudové služby Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Opětovné přidání role do projektu cloudové služby Azure
Pokud odeberete roli z projektu cloudové služby, ale později se rozhodnete přidat roli zpět do projektu, budou přidány pouze deklarace role a základní atributy, jako jsou koncové body a diagnostické informace. Do souboru ani do souboru `ServiceDefinition.csdef` `ServiceConfiguration.cscfg` nejsou přidány žádné další prostředky ani odkazy. Chcete-li tyto informace přidat, je třeba je do těchto souborů přidat ručně.

Můžete například odebrat roli webové služby a později se rozhodnete přidat tuto roli zpět do řešení. Pokud tak učiníte, dojde k chybě. Chcete-li této chybě zabránit, `<LocalResources>` je třeba přidat prvek `ServiceDefinition.csdef` zobrazený v následujícím jazyce XML zpět do souboru. Použijte název role webové služby, kterou jste přidali zpět do projektu jako součást atributu name pro element ** \<LocalStorage>.** V tomto příkladu je název role webové služby **WCFServiceWebRole1**.

```xml
<WebRole name="WCFServiceWebRole1">
    <Sites>
      <Site name="Web">
        <Bindings>
          <Binding name="Endpoint1" endpointName="Endpoint1" />
        </Bindings>
      </Site>
    </Sites>
    <Endpoints>
      <InputEndpoint name="Endpoint1" protocol="http" port="80" />
    </Endpoints>
    <Imports>
      <Import moduleName="Diagnostics" />
    </Imports>
    <LocalResources>
      <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
    </LocalResources>
</WebRole>
```

## <a name="next-steps"></a>Další kroky
- [Konfigurace rolí pro cloudovou službu Azure pomocí Sady Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
