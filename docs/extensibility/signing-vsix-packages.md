---
title: Podepisování balíčků VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2e97845c7ef17476e18e0068663772341ad8eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983116"
---
# <a name="signing-vsix-packages"></a>Podepisování balíčků VSIX
Sestavení rozšíření nemusí být podepsána předtím, než mohou běžet v aplikaci Visual Studio, ale je dobrým zvykem.

 Pokud chcete zabezpečit rozšíření a zajistit, aby nebylo manipulováno s, můžete přidat digitální podpis do balíčku VSIX. Když je VSIX podepsaný, zobrazí instalační program VSIX zprávu s oznámením, že je podepsán, a další informace o podpisu samotného. Pokud obsah VSIX byl změněn a VSIX nebyl znovu podepsán, instalační program VSIX zobrazí, že podpis není platný. Instalace není zastavena, ale uživatel je varován.

> [!IMPORTANT]
> Počínaje sadou Visual Studio 2015 budou balíčky VSIX podepsané pomocí jiného než SHA256 šifrování označeny jako neplatný podpis. Instalace VSIX není blokovaná, ale uživateli se zobrazí upozornění.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podepisování VSIX pomocí VSIXSignTool
 K dispozici je nástroj pro podpis SHA256 šifrování z [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na NuGet.org v [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Použití VSIXSignTool

1. Přidejte svůj VSIX do projektu.

2. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a **Vyberte &#124; přidat spravovat balíčky NuGet**.  Další informace o NuGet a přidání balíčků NuGet najdete v tématech [dokumentace k NuGet](/NuGet) a [uživatelské rozhraní Správce balíčků](/NuGet/Tools/Package-Manager-UI) .

3. Vyhledejte VSIXSignTool z VisualStudioExtensibility a nainstalujte balíček NuGet.

4. Nyní můžete spustit VSIXSignTool z umístění místních balíčků projektu. Projděte si nápovědu k příkazovému řádku tohoto nástroje pro váš scénář podpisu (VSIXSignTool. exe/?).

   Například pro podepsání souborem certifikátu chráněného heslem:

   VSIXSignTool. exe Sign/f \<certfile >/p \<password > \<VSIXfile >

## <a name="see-also"></a>Viz také:
- [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
