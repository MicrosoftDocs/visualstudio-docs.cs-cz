---
title: 'Postupy: zahrnutí požadavků do aplikace ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557674"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Postupy: Zahrnutí předpokladů s aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Předtím, než budete moci distribuovat požadovaný software do aplikace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], je nutné nejprve stáhnout instalační balíčky pro tyto požadavky do vašeho vývojového počítače. Když publikujete aplikaci a zvolíte možnost **Stáhnout požadavky ze stejného umístění jako moje aplikace**, dojde k chybě, pokud instalační balíčky nejsou ve složce **Packages** .  
  
> [!NOTE]
> Postup přidání instalačního balíčku pro .NET Framework najdete v tématu [Průvodce nasazením .NET Framework pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="Package"></a>Postup přidání instalačního balíčku pomocí souboru Package. XML  
  
1. V Průzkumníku souborů otevřete složku **balíčky** .  
  
     Ve výchozím nastavení je cesta C:\Program Files\Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages na 32ovém systému a C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages v 64 bitovém systému.  
  
2. Otevřete složku pro požadavek, který chcete přidat, a poté otevřete složku jazyka pro vaši nainstalovanou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (například **EN** pro angličtinu).  
  
3. V programu Poznámkový blok otevřete soubor **Package. XML** .  
  
4. Vyhledejte prvek **název** , který obsahuje `http://go.microsoft.com/fwlink`a zkopírujte adresu URL. Zahrňte část **LinkId** .  
  
    > [!NOTE]
    > Pokud žádný element **Name** neobsahuje `http://go.microsoft.com/fwlink`, otevřete soubor **Product. XML** v kořenové složce pro požadovanou součást a vyhledejte řetězec **fwlink** .  
  
    > [!IMPORTANT]
    > Některé požadované softwarové programy mohou mít několik instalačních balíčků (například v 32bitových nebo 64bitových systémech). Pokud více elementů **Name** obsahuje **fwlink**, je nutné zopakovat zbývající kroky pro každý z nich.  
  
5. Vložte adresu URL do panelu Adresa v prohlížeči a po zobrazení výzvy ke spuštění nebo uložení klikněte na **Uložit**.  
  
     Tento krok stáhne instalační soubor do počítače.  
  
6. Zkopírujte soubor do kořenové složky požadovaného softwaru.  
  
     V případě požadovaného softwaru Windows Installer 4.5 zkopírujte soubor do složky \Packages\WindowsInstaller4_5.  
  
     Nyní můžete instalační balíček distribuovat spolu s aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
