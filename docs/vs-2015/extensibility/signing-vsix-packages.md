---
title: Podepisování balíčků VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56ddcae38593d35bc8a31628bf3087dc79ca25c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732550"
---
# <a name="signing-vsix-packages"></a>Podepisování balíčků VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření sestavení není nutné před jejich spuštěním v sadě Visual Studio, ale je dobrým zvykem Uděláte to tak.  
  
 Pokud chcete zabezpečit vaše rozšíření a ujistěte se, že někdo nemanipuloval s, můžete přidat digitálního podpisu balíčku VSIX. Při podepsání VSIX instalátor VSIX se zobrazí zprávu s oznámením, že není podepsané, plus další informace o podpisu samotný. Pokud obsah VSIX byly změněny a VSIX nebyl znovu podepsán, instalátor VSIX se zobrazí, že podpis není platný. Instalace se zastaví, ale uživatel je upozorněn.  
  
> [!IMPORTANT]
>  Počínaje 2015, balíčků VSIX, které jsou podepsány pomocí nic jiného než SHA256 šifrování bude považovat za s neplatným podpisem. Instalace VSIX není blokován, ale uživatel zobrazí upozornění.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Podepsání souboru VSIX pomocí VSIXSignTool  
 Je SHA256 šifrování podepisování nástroj dostupný z [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) na nuget.org na [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Použít VSIXSignTool  
  
1. Přidejte do projektu VSIX.  
  
2. Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení vyberte **přidat &#124; spravovat balíčky NuGet**.  Další informace o NuGet a přidání NuGet balíčků naleznete v tématu [NuGet přehled](http://docs.nuget.org/) a [spravovat NuGet balíčky pomocí dialogového okna](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Vyhledejte VSIXSignTool z VisualStudioExtensibility a nainstalujte balíček NuGet.  
  
4. Nyní můžete spustit VSIXSignTool z umístění místního balíčky projektu. Najdete nápovědu k příkazovému řádku nástroje pro podepisování scénář (VSIXSignTool.exe /?).  
  
   Třeba když chcete přihlásit s heslem chráněná soubor certifikátu:  
  
   /F přihlašování VSIXSignTool.exe \<Soubor_certifikátu > /p \<heslo > \<VSIXfile >  
  
## <a name="see-also"></a>Viz také  
 [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

