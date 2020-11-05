---
title: Správa rolí v cloudových službách Azure
description: Naučte se přidávat a odebírat role v Azure Cloud Services pomocí sady Visual Studio.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 897cb36ee2afa650e042b92243c6044684468a6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398836"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Správa rolí v Azure Cloud Services pomocí sady Visual Studio
Až vytvoříte cloudovou službu Azure, můžete k ní přidat nové role nebo z ní odebrat stávající role. Můžete také importovat existující projekt a převést jej na roli. Například můžete importovat webovou aplikaci v ASP.NET a označit ji jako webovou roli.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Přidání role do cloudové služby Azure
Následující kroky vás provedou přidáním webové nebo pracovní role do projektu cloudové služby Azure v aplikaci Visual Studio.

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení** rozbalte uzel projektu.

1. Kliknutím pravým tlačítkem myši na uzel **role** zobrazte kontextovou nabídku. V místní nabídce vyberte **Přidat** a pak z aktuálního řešení vyberte existující webovou roli nebo roli pracovního procesu, nebo vytvořte projekt webové role nebo role pracovního procesu. Můžete také vybrat vhodný projekt, například projekt webové aplikace ASP.NET, a přidružit ho k projektu role.

   ![Možnosti nabídky pro přidání role do projektu cloudové služby Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Odebrání role z cloudové služby Azure
Následující kroky vás provedou odebráním webu nebo role pracovního procesu z projektu cloudové služby Azure v aplikaci Visual Studio.

1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

1. V **Průzkumník řešení** rozbalte uzel projektu.

1. Rozbalte uzel **role** .

1. Klikněte pravým tlačítkem na uzel, který chcete odebrat, a v místní nabídce vyberte **Odebrat**.

   ![Možnosti nabídky pro přidání role do cloudové služby Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Znovu přidání role do projektu cloudové služby Azure
Pokud odeberete roli z projektu cloudové služby, ale později se rozhodnete tuto roli přidat zpátky do projektu, přidají se jenom deklarace role a základní atributy, jako jsou koncové body a diagnostické informace. Do `ServiceDefinition.csdef` souboru nebo do souboru se nepřidaly žádné další prostředky ani odkazy `ServiceConfiguration.cscfg` . Pokud chcete přidat tyto informace, budete je muset ručně přidat zpátky do těchto souborů.

Můžete například odebrat roli webové služby a později se rozhodnout přidat tuto roli zpátky do svého řešení. Pokud to uděláte, dojde k chybě. Chcete-li této chybě zabránit, je nutné přidat `<LocalResources>` prvek zobrazený v následujícím kódu XML zpět do `ServiceDefinition.csdef` souboru. Použijte název role webové služby, kterou jste přidali zpět do projektu, jako součást atributu name **\<LocalStorage>** elementu. V tomto příkladu je název role webové služby **WCFServiceWebRole1**.

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
- [Konfigurace rolí pro cloudovou službu Azure pomocí sady Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
