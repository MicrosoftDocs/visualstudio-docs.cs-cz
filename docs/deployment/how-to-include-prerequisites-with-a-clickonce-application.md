---
title: 'Postupy: zahrnutí požadavků do aplikace ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ed90b9fcdd0c4ffe35789d00de4bbbd4aaa355
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557642"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Postupy: zahrnutí požadavků do aplikace ClickOnce
Předtím, než budete moci distribuovat požadovaný software do aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], je nutné nejprve stáhnout instalační balíčky pro tyto požadavky do vašeho vývojového počítače. Když publikujete aplikaci a zvolíte možnost **Stáhnout požadavky ze stejného umístění jako moje aplikace**, dojde k chybě, pokud instalační balíčky nejsou ve složce **Packages** .

> [!NOTE]
> Postup přidání instalačního balíčku pro .NET Framework najdete v tématu [Průvodce nasazením .NET Framework pro vývojáře](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="Package"></a>Postup přidání instalačního balíčku pomocí souboru Package. XML

1. V Průzkumníku souborů otevřete složku **balíčky** .

    Ve výchozím nastavení je cesta `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Otevřete složku pro požadavek, který chcete přidat, a poté otevřete složku jazyka pro vaši nainstalovanou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (například **EN** pro angličtinu).

3. V programu Poznámkový blok otevřete soubor *Package. XML* .

4. Vyhledejte prvek **název** , který obsahuje `http://go.microsoft.com/fwlink`a zkopírujte adresu URL. Zahrňte část **LinkId** .

   > [!NOTE]
   > Pokud žádný element **Name** neobsahuje `http://go.microsoft.com/fwlink`, otevřete soubor **Product. XML** v kořenové složce pro požadovanou součást a vyhledejte řetězec **fwlink** .

   > [!IMPORTANT]
   > Některé požadované softwarové programy mohou mít několik instalačních balíčků (například v 32bitových nebo 64bitových systémech). Pokud více elementů **Name** obsahuje **fwlink**, je nutné zopakovat zbývající kroky pro každý z nich.

5. Vložte adresu URL do panelu Adresa v prohlížeči a po zobrazení výzvy ke spuštění nebo uložení klikněte na **Uložit**.

    Tento krok stáhne instalační soubor do počítače.

6. Zkopírujte soubor do kořenové složky požadovaného softwaru.

    Například pro požadavek Instalační služba systému Windows 4,5 Zkopírujte soubor do složky *WindowsInstaller4_5 \Packages\* .

    Nyní můžete instalační balíček distribuovat spolu s aplikací.

## <a name="see-also"></a>Viz také
- [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
