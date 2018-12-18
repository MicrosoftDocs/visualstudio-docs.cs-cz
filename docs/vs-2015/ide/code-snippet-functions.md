---
title: Funkce fragmentu kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3874b162719deb02813ceb7eae09b373e208f458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270878"
---
# <a name="code-snippet-functions"></a>Funkce fragmentu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existují tři funkce, které jsou k dispozici pro použití s [!INCLUDE[csprcs](../includes/csprcs-md.md)] fragmenty kódu. Funkce jsou zadány v [funkce](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df) element fragmentu kódu. Informace o vytváření fragmenty kódu najdete v tématu [fragmenty kódu](../ide/code-snippets.md).  
  
## <a name="functions"></a>Funkce  
 Následující tabulka popisuje dostupné k použití s funkcí `Function` element ve fragmentech kódu.  
  
|Funkce|Popis|Jazyk|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Generuje příkazu switch a sadu příkazy case pro členy výčtu určené `EnumerationLiteral` parametru. `EnumerationLiteral` Parametr musí být odkaz na literál výčtu nebo typu výčtu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`ClassName()`|Vrací název třídy, která obsahuje vložený fragment kódu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Snižuje *TypeName* parametr své nejjednodušší podobě v kontextu, ve kterém se vyvolala fragmentu kódu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `GenerateSwitchCases` funkce. Při vložení tohoto fragmentu a výčet se zadá do `$switch_on$` literálu, `$cases$` generuje literál `case` prohlášení pro každou hodnotu ve výčtu.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `ClassName` funkce. Po vložení fragmentu kódu `$classname$` literálu se nahradí názvem ohraničující třídy v tomto umístění v souboru kódu.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití `SimpleTypeName` funkce. Při vložení fragmentu kódu do souboru kódu `$SystemConsole$` literál nahradí nejjednodušší forma <xref:System.Console> typ v kontextu, ve kterém se vyvolala fragmentu kódu.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce – Element (fragmenty kódu technologie Intellisense)](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Fragmenty kódu – odkaz schématu](../ide/code-snippets-schema-reference.md)



