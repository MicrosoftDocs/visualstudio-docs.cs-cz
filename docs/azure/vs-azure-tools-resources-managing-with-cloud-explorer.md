---
title: Správa prostředků Azure pomocí průzkumníka cloudu | Microsoft Docs
description: Naučte se používat Průzkumníka cloudu k procházení a správě prostředků Azure v Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 775045247cda106d31cf1517e727b9dda5142c4f
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038613"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Správa prostředků přidružených k účtům Azure v Průzkumníkovi cloudu sady Visual Studio

::: moniker range=">=vs-2022"
> [!Important]
> Průzkumník cloudu byl ve Visual Studio 2022 vyřazen. Místo toho můžete použít následující alternativy:
> - Použití [Průzkumník služby Microsoft Azure Storage](/azure/vs-azure-tools-storage-manage-with-storage-explorer) je bezplatná samostatná aplikace od Microsoftu. Můžete ho použít k vizuální práci s daty Azure Storage Windows, macOS a Linuxu.
> - Konzola [Kudu poskytuje](https://github.com/projectkudu/kudu/wiki/Kudu-console) přímý přístup z příkazového řádku se zvýšenými oprávněními App Service serveru a jeho systému souborů. Jde o cenný ladicí nástroj a umožňuje operace rozhraní příkazového řádku, jako je instalace balíčků.
>
> V případě potřeby můžete použít Azure Portal nebo pokračovat v používání uzlu Azure Průzkumník serveru předchozích verzích Visual Studio.
>
> Další informace o verzi Visual Studio 2022 najdete v naší zprávě [k vydání verze.](/visualstudio/releases/2022/release-notes-preview/)

::: moniker-end

::: moniker range="<=vs-2019"

Průzkumník cloudu umožňuje zobrazit prostředky a skupiny prostředků Azure, kontrolovat jejich vlastnosti a provádět klíčové diagnostické akce vývojářů v rámci Visual Studio.

Stejně jako [Azure Portal](https://portal.azure.com)je Průzkumník cloudu postavený na Azure Resource Manager kódu. Proto Průzkumník cloudu rozumí prostředkům, jako jsou skupiny prostředků Azure a služby [](/azure/role-based-access-control/role-assignments-portal) Azure, jako jsou aplikace logiky a aplikace API, a podporuje řízení přístupu na základě role (RBAC).

## <a name="prerequisites"></a>Požadavky

* Visual Studio 2017 nebo novější (viz [stažení Visual Studio)](https://visualstudio.microsoft.com/downloads)s **vybranou úlohou Azure.** Můžete také použít starší verzi Visual Studio s Microsoft Azure SDK pro .NET [2.9.](https://www.microsoft.com/download/details.aspx?id=51657)
* Microsoft Azure účtu – Pokud účet nemáte, můžete si [](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) zaregistrovat bezplatnou zkušební verzi nebo si aktivovat výhody [předplatitele Visual Studio předplatného.](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)

> [!NOTE]
> Pokud chcete zobrazit Průzkumníka cloudu, aktivujte stisknutím **kláves Ctrl** Q vyhledávací pole a pak zadejte Průzkumník +  **cloudu.**

## <a name="add-an-azure-account-to-cloud-explorer"></a>Přidání účtu Azure do Průzkumníka cloudu

Pokud chcete zobrazit prostředky přidružené k účtu Azure, musíte ho nejprve přidat do **Průzkumníka cloudu.**

1. V **Průzkumníku cloudu** vyberte **tlačítko Správa** účtu.

   ![Ikona nastavení účtu Azure v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Vyberte **Spravovat účty.**

   ![Odkaz na přidání účtu v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Přihlaste se k účtu Azure, jehož prostředky chcete procházet.

1. Po přihlášení k účtu Azure se zobrazí předplatná přidružená k tomuto účtu. Zaškrtněte políčka u předplatných účtů, která chcete procházet, a pak vyberte **Použít.**

   ![Průzkumník cloudu: Vyberte předplatná Azure, která se zobrazí.](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Po výběru předplatných, jejichž prostředky chcete procházet, se tato předplatná a prostředky zobrazí v **Průzkumníku cloudu.**

   ![Výpis prostředků Průzkumníka cloudu pro účet Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Odebrání účtu Azure z Průzkumníka cloudu

1. V **Průzkumníku cloudu** vyberte **Správa účtů.**

   ![Nastavení účtu Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Vedle účtu, který chcete odebrat, vyberte **Spravovat účty**.

   ![Odebrání účtu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Pokud **chcete účet** odebrat, zvolte Odebrat.

    ![Dialogové okno Správa účtů v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Zobrazení typů prostředků nebo skupin prostředků

Pokud chcete zobrazit prostředky Azure, můžete zvolit zobrazení **Typy prostředků** nebo **Skupiny** prostředků.

1. V **Průzkumníku** cloudu vyberte rozevírací seznam zobrazení prostředků.

   ![Rozevírací seznam Průzkumník cloudu pro výběr požadovaného zobrazení prostředků](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. V místní nabídce vyberte požadované zobrazení:

   * **Zobrazení Typy** prostředků – běžné zobrazení použité v [Azure Portal](https://portal.azure.com)zobrazuje prostředky Azure zařazené do kategorií podle jejich typu, jako jsou webové aplikace, účty úložiště a virtuální počítače.
   * **Zobrazení Skupiny** prostředků – kategorizuje prostředky Azure podle skupiny prostředků Azure, ke které jsou přidružené. Skupina prostředků je sada prostředků Azure, kterou obvykle používá konkrétní aplikace. Další informace o skupinách prostředků Azure najdete v [Azure Resource Manager přehledu.](/azure/azure-resource-manager/resource-group-overview)

   Následující obrázek ukazuje porovnání těchto dvou zobrazení prostředků:

   ![Porovnání zobrazení prostředků v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Zobrazení a procházení prostředků v Průzkumníku cloudu

Pokud chcete přejít k prostředku Azure a zobrazit jeho informace v Průzkumníku cloudu, rozbalte typ položky nebo přidruženou skupinu prostředků a pak prostředek vyberte. Když vyberete prostředek, zobrazí se informace na dvou kartách **– Akce** a **Vlastnosti** – v dolní části Průzkumníka cloudu.

* **Karta** Akce – zobrazuje seznam akcí, které můžete pro vybraný prostředek provádět v Průzkumníku cloudu. Tyto možnosti můžete zobrazit také tak, že kliknete pravým tlačítkem na prostředek a zobrazíte jeho místní nabídku.

* **Karta** Vlastnosti – zobrazuje vlastnosti prostředku, například jeho typ, národní prostředí a skupinu prostředků, ke kterým je přidružený.

Následující obrázek ukazuje příklad porovnání toho, co vidíte na každé kartě pro App Service:

  ![Snímek obrazovky s Průzkumníkem cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Každý prostředek má akci **Otevřít na portálu**. Když zvolíte tuto akci, Průzkumník cloudu zobrazí vybraný prostředek v Azure Portal [.](https://portal.azure.com) Funkce **Otevřít na portálu** je po ruce pro navigaci k hluboko vnořeným prostředkům.

V závislosti na prostředku Azure se dají zobrazit také další akce a hodnoty vlastností. Například webové aplikace a aplikace logiky  mají kromě možnosti Otevřít na portálu také akce Otevřít v prohlížeči a Připojit **ladicí** **program.** Akce pro otevření editorů se zobrazí, když zvolíte objekt blob, frontu nebo tabulku účtu úložiště. Aplikace Azure mají **vlastnosti adresy URL** a **stavu,** zatímco prostředky úložiště mají vlastnosti klíče a připojovacího řetězce.

## <a name="find-resources-in-cloud-explorer"></a>Hledání prostředků v Průzkumníku cloudu

Pokud chcete ve svých předplatných účtů Azure vyhledat prostředky s konkrétním názvem, zadejte název do vyhledávacího pole **v** **Průzkumníku cloudu.**

  ![Hledání prostředků v Průzkumníku cloudu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Při zadávání znaků do **vyhledávacího** pole se ve stromu prostředků zobrazí pouze prostředky, které se shodují s těmito znaky.

::: moniker-end
