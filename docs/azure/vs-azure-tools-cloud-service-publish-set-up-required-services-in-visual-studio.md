---
title: Příprava na publikování nebo nasazení cloudové služby
description: Naučte se postupy nastavení služeb cloudu a účtu úložiště a konfiguraci aplikace Azure.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: f6174f8294f3a9e990893ca9a45d77f2a069692e
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489659"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Příprava na publikování nebo nasazení cloudové služby v sadě Visual Studio

Chcete-li publikovat projekt cloudové služby, musíte nastavit následující služby, jak je popsáno v tomto článku:

* **Cloudová služba** pro spuštění vašich rolí v prostředí Azure a
* **Účet úložiště,** který poskytuje přístup ke službám objektů blob, fronty a tabulky.

## <a name="create-a-cloud-service"></a>Vytvoření cloudové služby

Cloudová služba spouští vaše role v prostředí Azure. Cloudovou službu můžete vytvořit buď ve Visual Studiu nebo prostřednictvím [portálu Azure,](https://portal.azure.com/) jak je popsáno v následujících částech.

### <a name="create-a-cloud-service-from-visual-studio"></a>Vytvoření cloudové služby z Visual Studia

1. U dříve vytvořeného projektu cloudové služby klikněte pravým tlačítkem myši na položku **Publikovat**.
1. V případě potřeby se přihlaste pomocí účtu Microsoft nebo organizace přidruženého k vašemu předplatnému Azure a pak vyberte **Další** a přejděte na stránku **Nastavení.**
1. Zobrazí se dialogové okno **Vytvořit účet cloudové služby a úložiště** (pokud ne, vyberte vytvořit **nový** ze seznamu **Služby Cloud).**
1. Zadejte název bez rozlišování velkých a malých písmen pro cloudovou službu, která je součástí adresy URL a musí být jedinečná. Zvolte také oblast nebo skupinu spřažení a vyberte možnost Replikace.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Vytvoření cloudové služby prostřednictvím portálu Azure

1. Přihlaste se k webu [Azure Portal](https://portal.azure.com/).
1. Na levé straně stránky vyberte **Cloudservices (klasické).**
1. Vyberte **+ Přidat**a zadejte požadované informace (název DNS, odběr, skupina prostředků a umístění). V tomto okamžiku není nutné nahrát balíček, protože to uděláte později v sadě Visual Studio.
1. Vyberte **Vytvořit,** chcete-li proces dokončit.

## <a name="create-a-storage-account"></a>vytvořit účet úložiště

Účet úložiště poskytuje přístup ke službám objektů blob, fronty a tabulky. Účet úložiště můžete vytvořit prostřednictvím Visual Studia nebo [portálu Azure](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Vytvoření účtu úložiště z Visual Studia

1. V **Průzkumníku řešení** s dříve vytvořeným projektem cloudové služby vyhledejte uzel **Připojené služby** v rámci projektu role, klikněte pravým tlačítkem myši a vyberte **Přidat připojenou službu**. (V Visual Studiu 2015 klikněte pravým tlačítkem myši na uzel **úložiště** a vyberte **Vytvořit účet úložiště**.)
1. V seznamu **Připojené služby,** který se zobrazí, vyberte **Cloudové úložiště s Azure Storage**.
1. V dialogovém okně Azure Storage, které se zobrazí, vyberte **+Vytvořit nový účet úložiště**, který vyvolá dialogové okno, ve kterém zadáte předplatné, název pro účet, cenovou úroveň, skupinu prostředků a umístění.
1. Až budete hotovi, vyberte **Vytvořit.** Nový účet úložiště se zobrazí v seznamu dostupných účtů úložiště ve vašem předplatném.
1. Vyberte tento účet a vyberte **Přidat**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Vytvoření účtu úložiště prostřednictvím portálu Azure

1. Přihlaste se k webu [Azure Portal](https://portal.azure.com/).
1. V levém horním rohu vyberte **+ Nový.**
1. V **Storage** části "Azure Marketplace" vyberte **Účet úložiště – objekt blob, soubor, tabulka, fronta** z pravé strany.
1. Zadejte požadované informace (název, model nasazení a tak dále.
1. Vyberte **Vytvořit,** chcete-li proces dokončit.

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurace aplikace tak, aby používala účet úložiště

Po vytvoření účtu úložiště připojení k němu z Visual Studia automaticky aktualizuje konfigurace služby pro projekt, včetně adres URL a přístupových klíčů.

Pokud jste vytvořili cloudovou službu z Visual Studia pomocí přidat `ServiceConfiguration.Cloud.cscfg` `ServiceConfiguration.Local.cscfg` **připojenou službu**, můžete zkontrolovat připojení otevřením a .

Pokud jste vytvořili cloudovou službu prostřednictvím portálu Azure, postupujte podle stejných kroků v [části Vytvoření účtu úložiště z Visual Studia,](#create-a-storage-account-from-visual-studio) ale místo vytvoření nového účtu vyberte existující účet. Visual Studio pak aktualizuje konfiguraci za vás.

Chcete-li konfigurovat nastavení ručně, použijte stránky vlastností v sadě Visual Studio pro příslušnou roli v projektu cloudové služby (klikněte pravým tlačítkem myši na roli a vyberte **vlastnosti**). Další informace naleznete [v tématu Konfigurace připojovacího řetězce k účtu úložiště](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>O přístupových klíčích

Na portálu Azure se zobrazují adresy URL, které můžete použít pro přístup k prostředkům v každé službě úložiště Azure a také primární a sekundární přístupové klíče pro váš účet. Tyto klíče slouží k ověření požadavků proti služby úložiště.

Sekundární přístupový klíč poskytuje stejný přístup k vašemu účtu úložiště jako primární přístupový klíč a je generován jako záloha v případě ohrožení primárního přístupového klíče. Dále se doporučuje pravidelně obnovovat přístupové klíče. Nastavení připojovacího řetězce můžete upravit tak, aby při regenerování primárního klíče používalo sekundární klíč, a pak jej můžete upravit tak, aby používal obnovený primární klíč při regeneraci sekundárního klíče.

## <a name="next-steps"></a>Další kroky

Další informace o publikování aplikací do Azure z Visual Studia najdete v [tématu Publikování cloudové služby pomocí nástrojů Azure](vs-azure-tools-publishing-a-cloud-service.md).
