---
title: Barva kompilátoru VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144327"
---
# <a name="vsix-color-compiler"></a>Barva kompilátoru VSIX
Nástroj Visual Studio rozšíření barva kompilátoru je konzolovou aplikaci, která přebírá souboru .xml představující barvy pro existující sady Visual Studio motivy a převede ji na .pkgdef souboru tak, aby tyto barvy lze použít v sadě Visual Studio. Protože se snadno porovnat rozdíly mezi soubory .xml, tento nástroj je užitečný pro správu vlastních barev ve správě zdrojového kódu. Je také můžete jazyka do prostředí sestavení tak, aby výstup sestavení je soubor platný .pkgdef.  
  
 **Schéma XML motivu**  
  
 Soubor .xml dokončení motiv vypadá takto:  
  
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
  
 \<Motiv > element definuje celý motivu. Motiv musí obsahovat alespoň jeden \<kategorie > elementu. Motiv elementy jsou definovány takto:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Vyžaduje] Název motivu|  
|GUID|[Vyžaduje] Identifikátor GUID v motivu (musí se shodovat formátování identifikátor GUID)|  
  
 Při vytváření vlastních barev pro sadu Visual Studio, barvy, musí být definované pro následující motivů. Pokud neexistují žádné barvy pro konkrétní motiv, Visual Studio se pokusí načíst chybějící barvy z motiv světlý.  
  
|||  
|-|-|  
|**Název motivu**|**Motiv GUID**|  
|Lehký|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Tmavý|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|modrá|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Vysoký kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategorie**  
  
 \<Kategorie > element definuje sadu barev v motivu. Názvy kategorií poskytují logické seskupení a by měl být definován jako úzce nejblíže. Kategorie musí obsahovat alespoň jeden \<barva > elementu. Kategorie elementy jsou definovány takto:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Vyžaduje] Název kategorie|  
|GUID|[Vyžaduje] Kategorie GUID (musí se shodovat formátování identifikátor GUID)|  
  
 **Barva**  
  
 \<Barva > element definuje barvu, součásti nebo stav uživatelského rozhraní. Upřednostňované schéma pojmenování pro barvu, která je [uživatelského rozhraní typ] [stavu]. Nepoužívejte slovo "Barva,", protože je redundantní. Barvu, která by měla jasně označuje typ elementu a situace nebo "stavu", pro které se použijí barvu. Barvu, která nesmí být prázdný a musí obsahovat jedno nebo obě \<pozadí > a \<popředí > elementu. Barva elementy jsou definovány takto:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Název|[Vyžaduje] Název barvy|  
  
 **Pozadí nebo popředí**  
  
 \<Pozadí > a \<popředí > elementy zadejte hodnotu a typ pro pozadí nebo popředí prvku uživatelského rozhraní barvy. Tyto prvky mít žádné podřízené objekty.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atribut**|**Definice**|  
|Typ|[Vyžaduje] Typ barvy. Může být jeden z následujících akcí:<br /><br /> *CT_INVALID:* barvu je neplatný nebo není nastavená.<br /><br /> *CT_RAW:* nezpracovanou hodnotu ARGB.<br /><br /> *CT_COLORINDEX:* NEPOUŽÍVEJTE.<br /><br /> *CT_SYSCOLOR:* barvy systému Windows z SysColor.<br /><br /> *CT_VSCOLOR:* Visual Studio barvu ze __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* automatické barvu.<br /><br /> *CT_TRACK_FOREGROUND:* NEPOUŽÍVEJTE.<br /><br /> *CT_TRACK_BACKGROUND:* NEPOUŽÍVEJTE.|  
|Zdroj|[Vyžaduje] Hodnota barvy v šestnáctkové číslo|  
  
 Jsou podporovány všechny hodnoty výčtu __VSCOLORTYPE schéma v atributu typu. Doporučujeme však používat pouze CT_RAW a CT_SYSCOLOR.  
  
 **Všechny společně**  
  
 Toto je jednoduchý příklad souboru .xml platný motivu:  
  
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
  
## <a name="how-to-use-the-tool"></a>Postup použití nástroje  
 **Syntaxe**  
  
 VsixColorCompiler \<souboru XML > \<PkgDef soubor > \<volitelné argumenty >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Název přepínače**|**Poznámky**|**Požadované nebo volitelné**|  
|Nepojmenované (soubor XML)|Toto je první nepojmenovaný parametr a je cesta k souboru XML pro převod.|Požadováno|  
|Nepojmenované (.pkgdef soubor)|Toto je druhý nepojmenovaný parametr a je výstupní cesta k souboru generovaného .pkgdef.<br /><br /> Výchozí hodnota: \<název souboru XML > .pkgdef|Nepovinné|  
|/ nologo|Nastavením tohoto příznaku zastaví informace o produktu a autorských právech v tisku.|Nepovinné|  
|/?|Vytiskněte informace nápovědy.|Nepovinné|  
|/help|Vytiskněte informace nápovědy.|Nepovinné|  
  
 **Příklady**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Poznámky  
  
-   Tento nástroj vyžaduje nainstalované nejnovější verzi modulu runtime VC ++.  
  
-   Jsou podporovány pouze jeden soubory. Hromadný převod prostřednictvím cesty ke složce zadat není podporován.  
  
## <a name="sample-output"></a>Ukázkový výstup  
 Soubor .pkgdef generovaný nástrojem bude vypadat podobně jako následující klíče:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```