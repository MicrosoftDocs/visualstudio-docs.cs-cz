---
title: 'Postupy: Přidání závislosti do balíčku VSIX | Microsoft Docs'
description: Naučte se, jak nastavit nasazení balíčku VSIX, které nainstaluje všechny závislosti, které ještě nejsou v cílovém počítači přítomné.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d7ef19bafd0788ed15094979141679625e4e992f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993832"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Postupy: Přidání závislosti k balíčku VSIX

Můžete nastavit nasazení balíčku VSIX, které nainstaluje všechny závislosti, které ještě nejsou k dispozici v cílovém počítači. Chcete-li to provést, zahrňte do souboru *source. extension. vsixmanifest* závislosti VSIX.

## <a name="to-add-a-dependency"></a>Přidání závislosti

1. Otevřete soubor *source. extension. vsixmanifest* v zobrazení **Návrh** . Přejděte na kartu **závislosti** a klikněte na **Nový**.

2. Přidání nainstalovaného rozšíření: v dialogovém okně **Přidat novou závislost** vyberte možnost **nainstalovaná rozšíření** a potom v rozevíracím seznamu **název** vyberte rozšíření v seznamu.

3. Chcete-li přidat další VSIX, který není nainstalován: v dialogovém okně **Přidat novou závislost** vyberte v **systému souborů možnost soubor** a poté pomocí tlačítka **Procházet** vyberte VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Vyžadovat konkrétní verzi sady Visual Studio

Pokud vaše rozšíření vyžaduje konkrétní verzi sady Visual Studio 2017, závisí například na funkci vydané v 15,3, můžete zadat číslo sestavení v souboru VSIX **InstallationTarget**. Například verze 15,3 má číslo buildu "15.0.26730.3". [Tady](../install/visual-studio-build-numbers-and-release-dates.md)vidíte mapování verzí k sestavování čísel. Všimněte si, že použití čísla vydané verze 15,3 nebude fungovat správně.

Pokud vaše rozšíření vyžaduje 15,3 nebo vyšší, deklarujete **verzi InstallationTarget** jako [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller detekuje starší verze sady Visual Studio a informuje uživatele o tom, že je požadována pozdější aktualizace.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Příprava rozšíření pro nasazení Instalační služba systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)