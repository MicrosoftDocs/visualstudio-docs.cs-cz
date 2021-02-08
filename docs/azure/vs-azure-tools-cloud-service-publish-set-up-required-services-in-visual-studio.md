---
title: Příprava na publikování nebo nasazení cloudové služby
description: Naučte se postup nastavení služeb cloudu a účtu úložiště a konfiguraci aplikace Azure.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 06157f1476762af5bfe24ce950e29e80ac60e6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844421"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Příprava na publikování nebo nasazení cloudové služby v sadě Visual Studio

Chcete-li publikovat projekt cloudové služby, musíte nastavit následující služby, jak je popsáno v tomto článku:

* **Cloudová služba** pro spouštění vašich rolí v prostředí Azure a
* **Účet úložiště** , který poskytuje přístup ke službám blob, Queue a Table.

## <a name="create-a-cloud-service"></a>Vytvoření cloudové služby

Cloudová služba spouští vaše role v prostředí Azure. Cloudovou službu můžete vytvořit buď v aplikaci Visual Studio, nebo prostřednictvím [Azure Portal](https://portal.azure.com/) , jak je popsáno v následujících částech.

### <a name="create-a-cloud-service-from-visual-studio"></a>Vytvoření cloudové služby ze sady Visual Studio

1. V dříve vytvořeném projektu cloudové služby klikněte pravým tlačítkem na projekt vybrat **publikovat**.
1. V případě potřeby se přihlaste pomocí účtu Microsoft nebo organizace přidruženého k vašemu předplatnému Azure a pak kliknutím na tlačítko **Další** přejděte na stránku **Nastavení** .
1. Zobrazí se dialogové okno **vytvořit cloudovou službu a účet úložiště** (Pokud ne, vyberte **vytvořit nový** ze seznamu **cloudové služby** ).
1. Zadejte pro cloudovou službu název nerozlišující malá a velká písmena, která tvoří část vaší adresy URL a musí být jedinečná. Zvolte také oblast nebo skupinu vztahů a vyberte možnost replikace.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Vytvoření cloudové služby prostřednictvím Azure Portal

1. Přihlaste se na [Azure Portal](https://portal.azure.com/).
1. Na levé straně stránky vyberte **Cloud Services (Classic)** .
1. Vyberte **+ Přidat** a zadejte požadované informace (název DNS, předplatné, skupina prostředků a umístění). V tomto okamžiku není nutné nahrávat balíček, protože to provedete později v aplikaci Visual Studio.
1. Pro dokončení procesu vyberte **vytvořit** .

## <a name="create-a-storage-account"></a>Vytvoření účtu úložiště

Účet úložiště poskytuje přístup ke službám blob, Queue a Table. Účet úložiště můžete vytvořit pomocí sady Visual Studio nebo [Azure Portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Vytvoření účtu úložiště ze sady Visual Studio

1. V **Průzkumník řešení** s dříve vytvořeným projektem cloudové služby vyhledejte uzel **připojené služby** v rámci projektu role, klikněte pravým tlačítkem myši a vyberte **Přidat připojenou službu**. (V aplikaci Visual Studio 2015 klikněte pravým tlačítkem myši na uzel **úložiště** a vyberte **vytvořit účet úložiště**.)
1. V seznamu **připojené služby** , který se zobrazí, vyberte **cloudové úložiště s Azure Storage**.
1. V zobrazeném dialogovém okně Azure Storage vyberte **+ vytvořit nový účet úložiště**, ve kterém se zobrazí dialogové okno, ve kterém můžete zadat předplatné, název účtu, cenovou úroveň, skupinu prostředků a umístění.
1. Až budete hotovi, vyberte **vytvořit** . V seznamu dostupných účtů úložiště ve vašem předplatném se zobrazí nový účet úložiště.
1. Vyberte tento účet a vyberte **Přidat**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Vytvořte účet úložiště pomocí Azure Portal

1. Přihlaste se na [Azure Portal](https://portal.azure.com/).
1. V levém horním rohu vyberte **+ Nový** .
1. V části "Azure Marketplace" vyberte **úložiště** **účet úložiště – objekt blob, soubor, tabulka, fronta** z pravé strany.
1. Zadejte požadované informace (název, model nasazení a tak dále).
1. Pro dokončení procesu vyberte **vytvořit** .

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurace aplikace tak, aby používala účet úložiště

Po vytvoření účtu úložiště se k němu připojíte ze sady Visual Studio a automaticky se aktualizují konfigurace služby pro projekt, včetně adres URL a přístupových klíčů.

Pokud jste vytvořili cloudovou službu ze sady Visual Studio pomocí **Přidat připojenou službu**, můžete ověřit připojení tak, že otevřete `ServiceConfiguration.Cloud.cscfg` a `ServiceConfiguration.Local.cscfg` .

Pokud jste vytvořili cloudovou službu prostřednictvím Azure Portal, postupujte podle stejných kroků v části [Vytvoření účtu úložiště ze sady Visual Studio](#create-a-storage-account-from-visual-studio) , ale místo vytvoření nového účtu vyberte existující účet. Visual Studio potom aktualizuje konfiguraci za vás.

Pokud chcete nakonfigurovat nastavení ručně, použijte stránky vlastností v aplikaci Visual Studio pro příslušnou roli v projektu cloudové služby (klikněte pravým tlačítkem na roli a vyberte **vlastnosti**). Další informace najdete v tématu [Konfigurace připojovacího řetězce k účtu úložiště](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>O přístupových klíčích

Azure Portal zobrazuje adresy URL, které můžete použít k přístupu k prostředkům v každé ze služeb Azure Storage, a také k primárním a sekundárním přístupovým klíčům pro váš účet. Tyto klíče použijete k ověření požadavků provedených u služby úložiště.

Sekundární přístupový klíč poskytuje stejný přístup k vašemu účtu úložiště jako primární přístupový klíč a vygeneruje se jako záloha, aby byl váš primární přístupový klíč zneužit. Kromě toho se doporučuje znovu vygenerovat přístupové klíče v pravidelných intervalech. Nastavení připojovacího řetězce můžete upravit tak, aby při opětovném generování primárního klíče používalo sekundární klíč, a pak ho můžete upravit tak, aby používalo znovu vygenerovaný primární klíč při opětovném vygenerování sekundárního klíče.

## <a name="next-steps"></a>Další kroky

Další informace o publikování aplikací do Azure ze sady Visual Studio najdete v tématu [publikování cloudové služby pomocí nástrojů Azure](vs-azure-tools-publishing-a-cloud-service.md).
