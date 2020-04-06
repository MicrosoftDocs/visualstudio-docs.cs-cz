---
title: Podepisování balíčků VSIX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700093"
---
# <a name="signing-vsix-packages"></a>Podepisování balíčků VSIX
Rozšíření sestavení není nutné podepsat před spuštěním v sadě Visual Studio, ale je vhodné tak učinit.

 Pokud chcete zabezpečit rozšíření a ujistěte se, že nebylo manipulováno, můžete přidat digitální podpis do balíčku VSIX. Při podpisu VSIX instalační ho vsix zobrazí zprávu označující, že je podepsána, plus další informace o samotném podpisu. Pokud byl změněn obsah VSIX a VSIX nebyl podepsán znovu, instalační program VSIX zobrazí, že podpis není platný. Instalace není zastavena, ale uživatel je upozorněn.

> [!IMPORTANT]
> Počínaje Visual Studio 2015, Balíčky VSIX podepsané pomocí jiného než sha256 šifrování budou identifikovány jako s neplatným podpisem. Instalace VSIX není blokována, ale uživatel bude upozorněn.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Podepisování VSIX pomocí nástroje VSIXSignTool
 K dispozici je sha256 šifrovací podpisový nástroj k dispozici od [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na nuget.org na [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Použití nástroje VSIXSignTool

1. Přidejte svůj VSIX do projektu.

2. Klikněte pravým tlačítkem myši na uzel projektu v Průzkumníku řešení a vyberte **přidat &#124; Spravovat balíčky NuGet**.  Další informace o NuGet a přidání balíčků NuGet naleznete [v dokumentaci NuGet](/NuGet) a témata [una v uzly správce balíčků.](/NuGet/Tools/Package-Manager-UI)

3. Vyhledejte nástroj VSIXSignTool z VisualStudioExtensibility a nainstalujte balíček NuGet.

4. Nyní můžete spustit VSIXSignTool z umístění místních balíčků projektu. Pro váš scénář podepisování (VSIXSignTool.exe /?) se podívejte do nápovědy k příkazovému řádku nástroje (VSIXSignTool.exe /?).

   Například k podpisu pomocí souboru certifikátu chráněného heslem:

   VSIXSignTool.exe sign \</f certfile \<> \</p heslo> VSIXfile>

## <a name="see-also"></a>Viz také
- [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
