---
title: Podepisování balíčků VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4efaaa78ce593d8b97d1df454a9c30c2e62d9f8
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918728"
---
# <a name="signing-vsix-packages"></a>Podepisování balíčků VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sestavení rozšíření nemusí být podepsána předtím, než mohou běžet v aplikaci Visual Studio, ale je dobrým zvykem.  
  
 Pokud chcete zabezpečit rozšíření a zajistit, aby nebylo manipulováno s, můžete přidat digitální podpis do balíčku VSIX. Když je VSIX podepsaný, zobrazí instalační program VSIX zprávu s oznámením, že je podepsán, a další informace o podpisu samotného. Pokud obsah VSIX byl změněn a VSIX nebyl znovu podepsán, instalační program VSIX zobrazí, že podpis není platný. Instalace není zastavena, ale uživatel je varován.  
  
> [!IMPORTANT]
> Počínaje 2015 budou balíčky VSIX podepsané pomocí jiného než SHA256 šifrování označeny jako neplatný podpis. Instalace VSIX není blokovaná, ale uživateli se zobrazí upozornění.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Podepisování VSIX pomocí VSIXSignTool  
 K dispozici je nástroj pro podpis SHA256 šifrování z [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) na NuGet.org v [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Použití VSIXSignTool  
  
1. Přidejte svůj VSIX do projektu.  
  
2. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a **Vyberte &#124; přidat spravovat balíčky NuGet**.  Další informace o NuGetu a přidání balíčků NuGet najdete v tématu [Přehled NuGet](/nuget/) a [Správa balíčků NuGet pomocí tohoto dialogového okna](/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Vyhledejte VSIXSignTool z VisualStudioExtensibility a nainstalujte balíček NuGet.  
  
4. Nyní můžete spustit VSIXSignTool z umístění místních balíčků projektu. Projděte si nápovědu k příkazovému řádku tohoto nástroje pro váš scénář podpisu (VSIXSignTool. exe/?).  
  
   Například pro podepsání souborem certifikátu chráněného heslem:  
  
   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>  
  
## <a name="see-also"></a>Viz také  
 [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
