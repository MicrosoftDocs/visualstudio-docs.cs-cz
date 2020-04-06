---
title: 'Postup: Přidání závislosti do balíčku VSIX | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711070"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Postup: Přidání závislosti do balíčku VSIX

Můžete nastavit nasazení balíčku VSIX, které nainstaluje všechny závislosti, které ještě nejsou v cílovém počítači k dispozici. Chcete-li to provést, zahrňte závislosti VSIX do souboru *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Přidání závislosti

1. Otevřete soubor *source.extension.vsixmanifest* v **návrhovém** zobrazení. Přejděte na kartu **Závislosti** a klepněte na **tlačítko Nový**.

2. Chcete-li přidat nainstalované rozšíření: v dialogovém okně **Přidat novou závislost** vyberte Možnost **Nainstalované rozšíření** a potom v yberte **Název**vyberte rozšíření v seznamu.

3. Chcete-li přidat další vsix, který není nainstalován: v dialogovém okně **Přidat novou závislost,** vyberte **soubor v systému souborů** a pak pomocí tlačítka **Procházet** vyberte VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Vyžadovat konkrétní verzi sady Visual Studio

Pokud vaše rozšíření vyžaduje konkrétní verzi Sady Visual Studio 2017, například závisí na funkci vydané v 15.3, můžete zadat číslo sestavení v VSIX **InstallationTarget**. Například verze 15.3 má číslo sestavení '15.0.26730.3'. Můžete vidět mapování verzí k sestavení čísla [zde](../install/visual-studio-build-numbers-and-release-dates.md). Všimněte si, že použití čísla verze '15.3' nebude fungovat správně.

Pokud vaše rozšíření vyžaduje 15.3 nebo vyšší, deklarujete **verzi InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller zjistí starší verze sady Visual Studio a informuje uživatele, že je vyžadována pozdější aktualizace.

## <a name="see-also"></a>Viz také

- [Odkaz na schéma rozšíření VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
