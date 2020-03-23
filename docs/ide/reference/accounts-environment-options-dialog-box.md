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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595901"
---
# <a name="accounts-environment-options-dialog-box"></a>Dialogové okno Účty, prostředí, možnosti

Na této stránce můžete nastavit různé možnosti související s účty, které používáte k přihlášení k sadě Visual Studio.

## <a name="personalization-account"></a>Účet individuálního nastavení

### <a name="synchronize-settings-across-devices"></a>Synchronizace nastavení mezi zařízeními

Tuto možnost použijte k určení, zda se má synchronizovat nastavení mezi více počítači. Další informace naleznete [v tématu Synchronizované nastavení](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Povolení toku kódu zařízení

Když je tato možnost vybraná, chování sady Visual Studio se změní, když vyberete **přidat účet** na stránce**Nastavení účtu** **souboru.** >  Místo zobrazení stránky **Přihlásit se ke svému účtu** se zobrazí dialogové okno s adresou URL a kódem, který chcete vložit do webového prohlížeče pro přihlášení. Tato možnost je užitečná v případech, kdy se nemůžete pravidelně přihlašovat k sadě Visual Studio, například pokud používáte starší verzi aplikace Internet Explorer nebo pokud brána firewall omezuje přístup. Další informace naleznete v [tématu Práce s více uživatelskými účty](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Registrované cloudy Azure

Tato část zobrazuje cloudové instance Azure, ke kterým máte přístup prostřednictvím jednoho nebo více účtů, které používáte k přihlášení k Visual Studiu. Můžete mít například přístup k privátní instanci Azure v datovém centru vaší společnosti. Nebo můžete mít přístup k suverénní nebo vládní instanci Azure, jako je Azure China 21 Vianet nebo Azure u.S. Government. Globální instance cloudu Azure se ve výchozím nastavení zobrazí v seznamu a nemůžete ji odebrat.

Zaregistrujte další cloud Azure výběrem tlačítka **Přidat.** V dialogovém okně **Přidat nový Azure Cloud** je uvedeno několik známých cloudových instancí Azure, ke kterému se můžete připojit, nebo můžete zadat adresu URL do privátního koncového bodu Azure.

![Přidání nové instance cloudu Azure](media/add-new-azure-cloud.png)

Po registraci dalšího cloudu Azure si můžete vybrat, do kterého cloudu Azure se chcete přihlásit, když se přihlásíte do Visual Studia.

## <a name="see-also"></a>Viz také

- [Synchronizace nastavení ve více počítačích](../synchronized-settings-in-visual-studio.md)
- [Přihlášení k sadě Visual Studio](../signing-in-to-visual-studio.md)
- [Práce s několika uživatelskými účty](../work-with-multiple-user-accounts.md)
- [Nastavení prostředí](../environment-settings.md)
