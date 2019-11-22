---
title: Prostředí (izolovaný nebo integrovaný režim) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db0ab2c2a97f7cedde5b9b3a5ab925467a25146
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300481"
---
# <a name="shell-isolated-or-integrated"></a>Prostředí (izolované nebo integrované)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastní aplikaci založenou na aplikaci Visual Studio můžete vytvořit v integrovaném nebo izolovaném režimu. V integrovaném režimu je kromě vaší aplikace k dispozici i mnoho funkcí sady Visual Studio. V izolovaném režimu zvolíte podmnožinu funkcí sady Visual Studio, kterou chcete distribuovat spolu s vlastním rozšířením.  
  
## <a name="integrated-mode"></a>Integrovaný režim  
 Integrovaný režim umožňuje uživatelům používat standardní funkce sady Visual Studio spolu s vlastními nástroji. Integrované prostředí je určeno hlavně pro hostování programovacích jazyků a nástrojů pro vývoj softwaru.  
  
 Vlastní nástroje, které jsou postavené na integrovaném prostředí, se automaticky sloučí s jakoukoli jinou verzí sady Visual Studio, která je nainstalovaná na stejném počítači. Pokud již není nainstalována aplikace Visual Studio, můžete poskytnout Distribuovatelný verzi integrovaného prostředí sady Visual Studio.  
  
 Redistribuovatelná verze integrovaného prostředí sady Visual Studio nezahrnuje programovací jazyky a funkce, které podporují jejich příslušné projektové systémy.  
  
> [!NOTE]
> Integrovaný režim prostředí sady Visual Studio lze nainstalovat společně se všemi edicemi sady Visual Studio s výjimkou edice Express.  
  
 Další informace najdete v tématu [Visual Studio Shell (integrovaný režim)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Izolovaný režim  
 Izolovaný režim umožňuje vytvářet vlastní nástroje, které jsou spouštěny souběžně s jinými verzemi sady Visual Studio. Je určena hlavně pro nástroje, které mají přístup ke službám Visual Studio bez závislosti na všech standardních funkcích sady Visual Studio. Můžete přizpůsobit vzhled aplikací postavených na izolovaném prostředí sady Visual Studio. Můžete snadno vypnout skupiny funkcí a příkazů nabídky, které nechcete spolu s vaší aplikací zobrazit.  
  
 Další informace najdete v tématu [izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuce integrované nebo izolované aplikace prostředí  
 Aby bylo možné distribuovat integrovanou nebo izolovanou aplikaci prostředí, je nutné zahrnout aplikaci, speciální integrovaný nebo izolovaný prostředí pro distribuci a instalační program. Další informace o distribuci a instalaci najdete v tématu [distribuce aplikací izolovaného prostředí](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> [Licenční smlouva s koncovým uživatelem (EULA)](https://www.visualstudio.com/support/legal/mt171552) pro integrované a izolované prostředí sady Visual Studio obsahuje oddíl pro shromažďování dat (**oddíl 3). Data**).  Popisuje údaje o využití zákazníka, které může společnost Microsoft shromažďovat od uživatelů integrovaného nebo izolovaného softwaru prostředí, který sestavíte do své aplikace. Další informace najdete v tématu [Microsoft Visual Studio prohlášení o zásadách ochrany osobních údajů pro produktovou řadu produktů](https://www.visualstudio.com/dn948229).  
> 
> Pokud shromažďujete oddělená data o využití od zákazníků prostřednictvím vaší aplikace, musíte poskytnout příslušné oznámení uživatelům vaší aplikace, kterou shromažďujete.  Když distribuujete software izolovaného nebo integrovaného prostředí v rámci vaší aplikace podle licence sady Visual Studio Software Development Kit, musíte zahrnout jednu z následujících možností:  
> 
> - Licenční smlouva s koncovým uživatelem v rámci licence aplikace  
> - vaše vlastní smlouva EULA, která vyžaduje, aby vaši zákazníci souhlasili s podmínkami ochrany integrovaného nebo izolovaného prostředí sady Visual Studio aspoň stejně jako licenční podmínky pro koncové uživatele Microsoftu pro software Shell  
  
## <a name="additional-resources"></a>Další prostředky  
 Další informace o redistribuovatelných balíčcích najdete na webu [Visual Studio rozšiřitelné soubory ke stažení](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="see-also"></a>Viz také  
 [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
