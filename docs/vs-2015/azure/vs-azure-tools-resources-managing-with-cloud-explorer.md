---
title: Správa prostředků Azure pomocí Průzkumníka cloudu | Microsoft Docs
description: Naučte se používat Průzkumníka cloudu k procházení a správě prostředků Azure v rámci sady Visual Studio.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 64d60c3a18338956d4d34b0406fff061970d2974
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850011"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Správa prostředků přidružených k účtům Azure v Průzkumníkovi cloudu sady Visual Studio

Průzkumník cloudu umožňuje zobrazit prostředky a skupiny prostředků Azure, zkoumat jejich vlastnosti a provádět klíčové vývojářské akce v rámci sady Visual Studio.

Podobně jako u [Azure Portal](https://portal.azure.com/)je Cloud Explorer postaven na Azure Resource Manager Stack. Proto Průzkumník cloudu rozumí prostředky, jako jsou skupiny prostředků Azure a služby Azure, jako jsou Logic Apps a API Apps, a podporuje [řízení přístupu na základě role](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2015 s [Microsoft Azure SDK pro .NET 2,9](https://www.microsoft.com/download/details.aspx?id=51657).
* Účet Microsoft Azure – Pokud účet nemáte, můžete si [zaregistrovat bezplatnou zkušební verzi](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/) nebo [aktivovat výhody pro předplatitele sady Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).

> [!NOTE]
> Průzkumníka cloudu zobrazíte tak, že na řádku nabídek vyberete **zobrazit** > **Průzkumník cloudu** .

## <a name="add-an-azure-account-to-cloud-explorer"></a>Přidat účet Azure do Průzkumníka cloudu

Pokud chcete zobrazit prostředky přidružené k účtu Azure, musíte nejdřív přidat účet do Průzkumníka cloudu.

1. V **Průzkumníku cloudu**vyberte **Nastavení účtu Azure**.

   ![Ikona nastavení účtu Azure v Průzkumníkovi cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Vyberte **Spravovat účty**.

   ![Odkaz na přidání účtu v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Přihlaste se k účtu Azure, jehož prostředky chcete procházet.

1. Po přihlášení k účtu Azure se zobrazí předplatná přidružená k tomuto účtu. Zaškrtněte políčka u předplatných účtů, která chcete procházet, a pak vyberte **použít**.

   ![Průzkumník cloudu: vyberte předplatná Azure, která chcete zobrazit.](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Po výběru předplatných, jejichž prostředky chcete procházet, se tyto odběry a prostředky zobrazí v Průzkumníku cloudu.

   ![Seznam prostředků v Průzkumníkovi cloudu pro účet Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Odebrání účtu Azure z Průzkumníka cloudu

1. V **Průzkumníku cloudu**vyberte **Správa účtů**.

   ![Ikona nastavení účtu Azure v Průzkumníkovi cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Vedle účtu, který chcete odebrat, vyberte **Spravovat účty**.

   ![Ikona nastavení účtu Azure v Průzkumníkovi cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Kliknutím na **Odebrat** odeberte účet.

    ![Dialogové okno Správa účtů v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Zobrazení typů prostředků nebo skupin prostředků

Pokud chcete zobrazit prostředky Azure, můžete zvolit **typy prostředků** nebo zobrazení **skupin prostředků** .

1. V **Průzkumníku cloudu**vyberte rozevírací seznam zobrazení prostředků.

   ![Rozevírací seznam Průzkumníka cloudu pro výběr zobrazení požadovaných prostředků](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. V místní nabídce vyberte požadované zobrazení:

   * Zobrazení **typů prostředků** – běžné zobrazení, které se používá na [Azure Portal](https://portal.azure.com/), zobrazuje vaše prostředky Azure v kategoriích podle jejich typu, jako jsou webové aplikace, účty úložiště a virtuální počítače.
   * Zobrazení **skupin prostředků** – kategorizuje prostředky Azure skupinou prostředků Azure, ke které jsou přidružené. Skupina prostředků je sada prostředků Azure, která se obvykle používá v konkrétní aplikaci. Další informace o skupinách prostředků Azure najdete v tématu [přehled Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).

   Následující obrázek znázorňuje porovnání dvou zobrazení prostředků:

   ![Porovnání zobrazení prostředků v Cloud Exploreru](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Zobrazení a navigace prostředků v Průzkumníkovi cloudu

Pokud chcete přejít do prostředku Azure a zobrazit jeho informace v Průzkumníku cloudu, rozbalte typ položky nebo přidruženou skupinu prostředků a pak vyberte prostředek. Když vyberete prostředek, zobrazí se informace na dvou kartách – **Akce** a **vlastnosti** – v dolní části Průzkumníka Cloud Exploreru.

* Karta **Akce** – obsahuje seznam akcí, které můžete provést v Průzkumníkovi cloudu pro vybraný prostředek. Tyto možnosti můžete zobrazit také tak, že kliknete pravým tlačítkem na prostředek a zobrazíte jeho kontextovou nabídku.

* Karta **vlastnosti** – zobrazí vlastnosti prostředku, jako je jeho typ, národní prostředí a skupina prostředků, ke kterým je přidružená.

Následující obrázek ukazuje příklad porovnání toho, co vidíte na jednotlivých kartách pro App Service:

  ![Snímek obrazovky Průzkumníka cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Každý prostředek má **otevřenou akci na portálu**. Když vyberete tuto akci, Průzkumník cloudu zobrazí vybraný prostředek v [Azure Portal](https://portal.azure.com/). Funkce **otevřít v portálu** je užitečná pro přechod na hluboce vnořené prostředky.

V závislosti na prostředku Azure se můžou objevit i další akce a hodnoty vlastností. Například webové aplikace a aplikace logiky mají kromě **otevření na portálu**také **otevřené akce v prohlížeči** a **připojení ladicího programu** . Akce otevření editory se zobrazí při výběru objektu blob, fronty nebo tabulky účtu úložiště. Aplikace Azure mají vlastnosti **Adresa URL** a **stav** , zatímco prostředky úložiště mají vlastnosti klíče a připojovacího řetězce.

## <a name="find-resources-in-cloud-explorer"></a>Najít prostředky v Průzkumníkovi cloudu

Pokud chcete v předplatných účtu Azure vyhledat prostředky s určitým názvem, zadejte název do **vyhledávacího** pole v Průzkumníku cloudu.

  ![Hledání prostředků v Průzkumníkovi cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Při zadávání znaků do **vyhledávacího** pole se ve stromu zdrojů zobrazí pouze prostředky, které odpovídají těmto znakům.
