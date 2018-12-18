---
title: 'Postupy: načtení informací řetězce dotazu do Online aplikace ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e8ad899d7cf62b2d874d5dc4971c8e7ad7f950a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829758"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Postupy: načtení informací řetězce dotazu do online aplikace ClickOnce
*Řetězec dotazu* je část adresy URL začínající otazník (?), který obsahuje libovolné informace ve formě *název = hodnota*. Předpokládejme, že máte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci s názvem `WindowsApp1` , která hostujete na `servername`, a vy chcete předávat hodnotu pro proměnnou `username` při spuštění aplikace. Vaše adresa URL může vypadat nějak takto:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Následující dva postupy ukazují, jak používat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace za účelem získání informací řetězce dotazu.  
  
> [!NOTE]
>  Pokud se spuštění vaší aplikace pomocí protokolu HTTP, namísto použití sdílené složky nebo místního systému souborů, můžete předat pouze informace v řetězci dotazu.  
  
 První procedura ukazuje jak vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace můžete použít malou část kódu ke čtení těchto hodnot při spuštění aplikace.  
  
 Následující postup ukazuje, jak nakonfigurovat váš [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci MageUI.exe tak, aby mohl přijímat parametry řetězce dotazu. Je potřeba to udělat pokaždé, když publikujete aplikaci.  
  
> [!NOTE]
>  Než provedete rozhodnutí pro tuto funkci povolit, najdete v části "Zabezpečení" dále v tomto tématu.  
  
 Informace o tom, jak vytvořit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení s použitím *Mage.exe* nebo *MageUI.exe*, naleznete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  Spuštění v rozhraní .NET Framework 3.5 SP1, je možné předat argumenty příkazového řádku pro offline [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. Pokud chcete zadat argumenty do aplikace, můžete předat parametry do souboru zástupce s. Rozšíření APPREF MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>K získání informací řetězce dotazu z aplikace ClickOnce  
  
1.  Umístěte následující kód ve vašem projektu. Aby tento kód funkce, budete muset mít odkaz na System.Web a přidejte `using` nebo `Imports` příkazy pro System.Web System.Collections.Specialized a System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Volání funkce definované dříve k načtení <xref:System.Collections.DictionaryBase.Dictionary%2A> z parametrů řetězce dotazu, který je indexované podle názvu.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Chcete-li povolit předávání do aplikace ClickOnce s MageUI.exe řetězce dotazů  
  
1. Otevřete okno příkazového řádku .NET a zadejte:  
  
   ```cmd  
   MageUI  
   ```  
  
2. Z **souboru** nabídce vyberte možnost **otevřete**a otevřete manifest nasazení pro váš [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, což je soubor končící na `.application` rozšíření.  
  
3. Vyberte **možnosti nasazení** panelu v levém navigačním okně a vyberte **parametry povolit adresu URL, které se mají předat aplikaci** zaškrtávací políčko.  
  
4. Z **souboru** nabídce vyberte možnost **Uložit**.  
  
> [!NOTE]
>  Alternativně můžete povolit předávání řetězce dotazů v [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Vyberte **parametry povolit adresu URL, které se mají předat aplikaci** zaškrtávací políčko, které lze najít otevřením **vlastnosti projektu**, vyberete **publikovat** kartu, kliknutím **Možnosti** tlačítko a pak vyberete **manifesty**.  
  
## <a name="robust-programming"></a>Robustní programování  
 Při použití parametrů řetězce dotazu, je třeba zadat pečlivě promyslet na tom, jak je aplikace nainstalovaná a aktivovaná. Pokud je aplikace nakonfigurována k instalaci na počítač uživatele z webu nebo ze sdílené síťové složce, je pravděpodobné, že uživatel aktivuje aplikaci jenom jednou prostřednictvím adresy URL. Poté uživatel obvykle aktivovat svoji aplikaci pomocí zástupce v **Start** nabídky. V důsledku toho vaše aplikace je zaručeno, že přijímat argumenty řetězce dotazu pouze jednou během celé jeho životnosti. Pokud budete chtít uložit tyto argumenty v počítači uživatele pro budoucí použití, zodpovídáte za jejich ukládáním do bezpečným a zabezpečeným způsobem.  
  
 Pokud vaše aplikace je online pouze, je vždy aktivovat prostřednictvím adresy URL. I v tomto případě však vaše aplikace musí být zapsané do fungovat správně, pokud jsou parametry řetězce dotazu chybí nebo je poškozený.  
  
## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework  
 Povolit předání parametrů adresy URL vašeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci pouze v případě, že máte v úmyslu čistí vstup všechny znaky škodlivý před jeho použitím. Řetězec vložených s uvozovky, lomítka nebo středníkem, třeba, můžou provádět operace s daty libovolného pokud použili nefiltrovaná v dotazu SQL na databázi. Další informace o zabezpečení řetězců dotazů, najdete v části [skript zneužije přehled](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)