---
title: Odkazy na možnosti účty
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a77a7ee6c9f9cdb545c5cbfb1c4fb7336ab19b70
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378104"
---
# <a name="accounts-environment-options-dialog-box"></a>Účty, prostředí, dialogové okno Možnosti

Pomocí této stránky můžete nastavit různé možnosti související s účty, které používáte k přihlášení k sadě Visual Studio.

## <a name="personalization-account"></a>Účet přizpůsobení

### <a name="synchronize-settings-across-devices"></a>Synchronizace nastavení mezi zařízeními

Tuto možnost použijte k určení, jestli se má nastavení synchronizovat napříč různými počítači. Další informace najdete v tématu [synchronizovaná nastavení](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Povolení toku kódu zařízení

Pokud je vybraná tato možnost, chování aplikace Visual Studio se změní při výběru **přidat účet** na **souboru** > **nastavení účtu** stránky. Místo toho, abyste **přihlásit ke svému účtu** stránky, zobrazí se dialogové okno, které poskytuje adresu URL a kód vložte do webového prohlížeče k přihlášení. Tato možnost je užitečná v případech, kde nemůžete se přihlásit k sadě Visual Studio regulární způsobem, například pokud používáte starší verzi aplikace Internet Explorer, nebo pokud brána firewall omezuje přístup. Další informace najdete v tématu [práce s několika uživatelskými účty](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Registrované cloudy Azure

Tato část ukazuje instance cloudu Azure, abyste měli přístup k prostřednictvím jednoho nebo více účtů, které používáte k přihlášení k sadě Visual Studio. Například můžete mít přístup k privátní instance Azure v datovém centru společnosti. Nebo můžete mít přístup k instanci suverénních nebo státní správu v Azure, jako je Azure China nebo Azure USA Státní správy. Ve výchozím nastavení v seznamu se zobrazí instance globálního cloudu Azure a nelze ji odstranit.

Registrace cloudu další Azure výběrem **přidat** tlačítko. **Přidat nový Cloud Azure** dialogové okno obsahuje několik instancí dobře známé cloudu Azure, můžete se připojit k, nebo můžete zadat adresu URL do privátního koncového bodu Azure.

![Přidat nové instance cloudu Azure](media/add-new-azure-cloud.png)

Až dokončíte registraci další cloudu Azure, můžete zvolit které cloudu Azure, budete chtít přihlásit po přihlášení k sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- [Synchronizace nastavení mezi více počítačů](../synchronized-settings-in-visual-studio.md)
- [Přihlášení k sadě Visual Studio](../signing-in-to-visual-studio.md)
- [Práce s několika uživatelskými účty](../work-with-multiple-user-accounts.md)
- [Nastavení prostředí](../environment-settings.md)
- [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md)