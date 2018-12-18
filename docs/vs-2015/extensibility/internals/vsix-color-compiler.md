---
title: Kompilátor barev VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19ca749b3ddd2190fd667ddb6c96c2a88c557999
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788430"
---
# <a name="vsix-color-compiler"></a>Kompilátor barev VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Je nástroj kompilátoru barva rozšíření Visual Studio konzolovou aplikaci, která přebírá soubor XML představující barvy pro existující motivů aplikace Visual Studio a převede jej .pkgdef souboru tak, aby tyto barvy, je možné v sadě Visual Studio. Protože jde snadno porovnat rozdíly mezi soubory .xml, tento nástroj je užitečný pro správu vlastních barev ve správě zdrojového kódu. Je také může využívat do prostředí sestavení tak, aby výstupy sestavení soubor .pkgdef platný.  
  
 **Schéma XML motivu**  
  
 Soubor XML motivu dokončení vypadá takto:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Motiv**  
  
 \<Motiv > element definuje celý motiv. Motiv musí obsahovat alespoň jeden \<kategorie > element. Motiv prvky jsou definovány takto:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Povinné] Název motivu|  
|GUID|[Povinné] Identifikátor GUID motivu (musí odpovídat identifikátoru GUID formátování)|  
  
 Při vytváření vlastní barvy pro sadu Visual Studio, musíte je definovat následující motivy tyto barvy. Pokud neexistují žádné barvy pro konkrétní motivu, Visual Studio se pokusí načíst chybějící barvy z světlý motiv.  
  
|||  
|-|-|  
|**Název motivu**|**Motiv GUID**|  
|Světlý|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Tmavý|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Modrá|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Vysoký kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategorie**  
  
 \<Kategorie > element definuje kolekci barvy motivu. Názvy kategorií zajišťují logické seskupení a musí být definován jako nejpřesnějším co nejvíc. Kategorie musí obsahovat alespoň jeden \<barva > element. Kategorie prvky jsou definovány takto:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Povinné] Název kategorie|  
|GUID|[Povinné] Identifikátor GUID kategorie (musí odpovídat identifikátoru GUID formátování)|  
  
 **Barva**  
  
 \<Barva > element definuje barvu, která pro fungování součásti nebo stavu uživatelského rozhraní. Upřednostňovaný schéma pojmenování pro barvu je [uživatelské rozhraní typu] [stav]. Nepoužívejte slova "color", protože je redundantní. Barva mělo jasně uvádět, typ elementu a situací nebo "stavu", pro které se použijí barvy. Barva nesmí být prázdné a musí obsahovat jeden nebo oba \<pozadí > a \<popředí > element. Barevné prvky jsou definovány takto:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Povinné] Název barvy|  
  
 **Na pozadí a/nebo popředí**  
  
 \<Pozadí > a \<popředí > elementy definovat hodnotu a typ pro pozadí nebo popředí prvku uživatelského rozhraní barvu. Tyto prvky nemají žádné podřízené položky.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Typ|[Povinné] Typ barvy. Může být jeden z následujících akcí:<br /><br /> *CT_INVALID:* barva je neplatný nebo není nastavená.<br /><br /> *CT_RAW:* nezpracované hodnoty ARGB.<br /><br /> *CT_COLORINDEX:* NEPOUŽÍVEJTE.<br /><br /> *CT_SYSCOLOR:* barvy systému Windows z SysColor.<br /><br /> *CT_VSCOLOR:* barvu sady Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Automatická barva.<br /><br /> *CT_TRACK_FOREGROUND:* NEPOUŽÍVEJTE.<br /><br /> *CT_TRACK_BACKGROUND:* NEPOUŽÍVEJTE.|  
|Zdroj|[Povinné] Hodnota barvy v šestnáctkovém|  
  
 Podporované výčtem __VSCOLORTYPE všechny hodnoty jsou podporovány na schéma v atributu typu. Doporučujeme však, že používáte pouze CT_RAW a CT_SYSCOLOR.  
  
 **Všechno dohromady**  
  
 Toto je jednoduchý příklad souboru XML motivu platné:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Jak používat nástroj  
 **Syntaxe**  
  
 VsixColorCompiler \<souboru XML > \<PkgDef soubor > \<volitelné argumenty >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Název přepínače**|**Poznámky**|**Požadované nebo volitelné**|  
|Nepojmenované (soubor XML)|Toto je první nepojmenovaný parametr a cesta k souboru XML pro převod.|Požadováno|  
|Nepojmenované (soubor .pkgdef)|Toto je druhá nepojmenovaný parametr a výstupní cesta k souboru generovaného .pkgdef.<br /><br /> Výchozí hodnota: \<název souboru XML > .pkgdef|volitelná,|  
|/ nologo|Informace o produktu a autorská práva tisk nastavení tohoto příznaku se zastaví.|volitelná,|  
|/?|Vytiskne informace nápovědy.|volitelná,|  
|/help|Vytiskne informace nápovědy.|volitelná,|  
  
 **Příklady**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Poznámky  
  
-   Tento nástroj vyžaduje instalaci nejnovější verze modulu runtime VC ++.  
  
-   Podporují se jenom jeden soubory. Hromadné byl inicializován převod pomocí cesty ke složkám se nepodporuje.  
  
## <a name="sample-output"></a>Ukázkový výstup  
 Soubor .pkgdef generovaný nástrojem bude vypadat podobně jako následující klíče:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```

