---
title: Odkaz na možnosti účtů
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595901"
---
# <a name="accounts-environment-options-dialog-box"></a>Účty, prostředí, dialogové okno Možnosti

Pomocí této stránky můžete nastavit různé možnosti týkající se účtů, které používáte k přihlášení do sady Visual Studio.

## <a name="personalization-account"></a>Účet přizpůsobení

### <a name="synchronize-settings-across-devices"></a>Synchronizovat nastavení mezi zařízeními

Tuto možnost použijte, chcete-li určit, zda chcete synchronizovat nastavení mezi více počítači. Další informace najdete v tématu [synchronizovaná nastavení](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Povolit tok kódu zařízení

Pokud je vybrána tato možnost, chování aplikace Visual Studio se změní po výběru možnosti **Přidat účet** na stránce > **Nastavení účtu** **souboru** . Namísto zobrazení na stránce **účtu** se zobrazí dialogové okno, které vám poskytne adresu URL a kód pro vložení do webového prohlížeče pro přihlášení. Tato možnost je užitečná v případech, kdy se nemůžete přihlásit k sadě Visual Studio běžným způsobem, například pokud používáte starší verzi Internet Exploreru nebo pokud brána firewall omezuje přístup. Další informace najdete v tématu [práce s několika uživatelskými účty](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Registrované cloudy Azure

V této části najdete informace o cloudových instancích Azure, ke kterým máte přístup, prostřednictvím jednoho nebo více účtů, které používáte k přihlášení do sady Visual Studio. Například můžete mít přístup k soukromé instanci Azure v datovém centru vaší společnosti. Nebo můžete mít přístup k instanci služby Azure svrchovaná nebo státní správy, jako je Azure Čína 21 Vianet nebo státní správa USA Azure. Globální cloudová instance Azure se v seznamu zobrazí ve výchozím nastavení a nemůžete ji odebrat.

Další cloud Azure zaregistrujete tak, že kliknete na tlačítko **Přidat** . V dialogu **Přidat nový cloud Azure** se zobrazí seznam několika dobře známých cloudových instancí Azure, ke kterým se můžete připojit, nebo můžete zadat adresu URL privátního koncového bodu Azure.

![Přidat novou instanci cloudu Azure](media/add-new-azure-cloud.png)

Po registraci dalšího cloudu Azure si můžete vybrat cloud Azure, ke kterému se chcete přihlašovat při přihlášení k aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- [Synchronizace nastavení mezi několika počítači](../synchronized-settings-in-visual-studio.md)
- [Přihlášení k sadě Visual Studio](../signing-in-to-visual-studio.md)
- [Práce s několika uživatelskými účty](../work-with-multiple-user-accounts.md)
- [Nastavení prostředí](../environment-settings.md)
