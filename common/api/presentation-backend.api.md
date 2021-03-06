## API Report File for "@bentley/presentation-backend"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { ClientRequestContext } from '@bentley/bentleyjs-core';
import { Content } from '@bentley/presentation-common';
import { ContentRequestOptions } from '@bentley/presentation-common';
import { Descriptor } from '@bentley/presentation-common';
import { DescriptorOverrides } from '@bentley/presentation-common';
import { DisplayValueGroup } from '@bentley/presentation-common';
import { DistinctValuesRequestOptions } from '@bentley/presentation-common';
import { EventSink } from '@bentley/imodeljs-backend';
import { HierarchyRequestOptions } from '@bentley/presentation-common';
import { Id64String } from '@bentley/bentleyjs-core';
import { IDisposable } from '@bentley/bentleyjs-core';
import { IModelDb } from '@bentley/imodeljs-backend';
import { InstanceKey } from '@bentley/presentation-common';
import { KeySet } from '@bentley/presentation-common';
import { LabelDefinition } from '@bentley/presentation-common';
import { LabelRequestOptions } from '@bentley/presentation-common';
import { Node } from '@bentley/presentation-common';
import { NodeKey } from '@bentley/presentation-common';
import { NodePathElement } from '@bentley/presentation-common';
import { Paged } from '@bentley/presentation-common';
import { PagedResponse } from '@bentley/presentation-common';
import { PartialHierarchyModification } from '@bentley/presentation-common';
import { PartialHierarchyModificationJSON } from '@bentley/presentation-common';
import { PresentationDataCompareOptions } from '@bentley/presentation-common';
import { PresentationUnitSystem } from '@bentley/presentation-common';
import { RegisteredRuleset } from '@bentley/presentation-common';
import { Ruleset } from '@bentley/presentation-common';
import { SelectionInfo } from '@bentley/presentation-common';
import { SelectionScope } from '@bentley/presentation-common';
import { SelectionScopeRequestOptions } from '@bentley/presentation-common';
import { UpdateInfoJSON } from '@bentley/presentation-common';
import { VariableValue } from '@bentley/presentation-common';
import { VariableValueJSON } from '@bentley/presentation-common';
import { VariableValueTypes } from '@bentley/presentation-common';

// @beta
export enum DuplicateRulesetHandlingStrategy {
    // (undocumented)
    Replace = 1,
    // (undocumented)
    Skip = 0
}

// @public
export class Presentation {
    static getManager(clientId?: string): PresentationManager;
    static getRequestTimeout(): number;
    static initialize(props?: PresentationProps): void;
    static get initProps(): PresentationPropsDeprecated | PresentationPropsNew | undefined;
    static terminate(): void;
}

// @beta
export enum PresentationBackendLoggerCategory {
    // (undocumented)
    Package = "presentation-backend",
    PresentationManager = "presentation-backend.PresentationManager",
    Rpc = "presentation-backend.Rpc"
}

// @beta
export enum PresentationBackendNativeLoggerCategory {
    // (undocumented)
    ECObjects = "ECObjects",
    // (undocumented)
    ECObjects_ECExpressions = "ECObjects.ECExpressions",
    // (undocumented)
    ECObjects_ECExpressions_Evaluate = "ECObjects.ECExpressions.Evaluate",
    // (undocumented)
    ECObjects_ECExpressions_Parse = "ECObjects.ECExpressions.Parse",
    // (undocumented)
    ECPresentation = "ECPresentation",
    // (undocumented)
    ECPresentation_Connections = "ECPresentation.Connections",
    // (undocumented)
    ECPresentation_RulesEngine = "ECPresentation.RulesEngine",
    // (undocumented)
    ECPresentation_RulesEngine_Content = "ECPresentation.RulesEngine.Content",
    // (undocumented)
    ECPresentation_RulesEngine_Localization = "ECPresentation.RulesEngine.Localization",
    // (undocumented)
    ECPresentation_RulesEngine_Navigation = "ECPresentation.RulesEngine.Navigation",
    // (undocumented)
    ECPresentation_RulesEngine_Navigation_Cache = "ECPresentation.RulesEngine.Navigation.Cache",
    // (undocumented)
    ECPresentation_RulesEngine_RulesetVariables = "ECPresentation.RulesEngine.RulesetVariables",
    // (undocumented)
    ECPresentation_RulesEngine_Threads = "ECPresentation.RulesEngine.Threads",
    // (undocumented)
    ECPresentation_RulesEngine_Update = "ECPresentation.RulesEngine.Update"
}

// @public
export class PresentationManager {
    constructor(props?: PresentationManagerProps);
    activeLocale: string | undefined;
    activeUnitSystem: PresentationUnitSystem | undefined;
    // (undocumented)
    compareHierarchies(requestContext: ClientRequestContext, requestOptions: PresentationDataCompareOptions<IModelDb>): Promise<PartialHierarchyModification[]>;
    computeSelection(requestContext: ClientRequestContext, requestOptions: SelectionScopeRequestOptions<IModelDb>, ids: Id64String[], scopeId: string): Promise<KeySet>;
    dispose(): void;
    getContent(requestContext: ClientRequestContext, requestOptions: Paged<ContentRequestOptions<IModelDb>>, descriptorOrOverrides: Descriptor | DescriptorOverrides, keys: KeySet): Promise<Content | undefined>;
    getContentAndSize(requestContext: ClientRequestContext, requestOptions: Paged<ContentRequestOptions<IModelDb>>, descriptorOrOverrides: Descriptor | DescriptorOverrides, keys: KeySet): Promise<{
        content: Content | undefined;
        size: number;
    }>;
    getContentDescriptor(requestContext: ClientRequestContext, requestOptions: ContentRequestOptions<IModelDb>, displayType: string, keys: KeySet, selection: SelectionInfo | undefined): Promise<Descriptor | undefined>;
    getContentSetSize(requestContext: ClientRequestContext, requestOptions: ContentRequestOptions<IModelDb>, descriptorOrOverrides: Descriptor | DescriptorOverrides, keys: KeySet): Promise<number>;
    getDisplayLabelDefinition(requestContext: ClientRequestContext, requestOptions: LabelRequestOptions<IModelDb>, key: InstanceKey): Promise<LabelDefinition>;
    getDisplayLabelDefinitions(requestContext: ClientRequestContext, requestOptions: LabelRequestOptions<IModelDb>, instanceKeys: InstanceKey[]): Promise<LabelDefinition[]>;
    getDistinctValues(requestContext: ClientRequestContext, requestOptions: ContentRequestOptions<IModelDb>, descriptor: Descriptor, keys: KeySet, fieldName: string, maximumValueCount?: number): Promise<string[]>;
    getFilteredNodePaths(requestContext: ClientRequestContext, requestOptions: HierarchyRequestOptions<IModelDb>, filterText: string): Promise<NodePathElement[]>;
    // @internal (undocumented)
    getNativePlatform: () => NativePlatformDefinition;
    getNodePaths(requestContext: ClientRequestContext, requestOptions: HierarchyRequestOptions<IModelDb>, paths: InstanceKey[][], markedIndex: number): Promise<NodePathElement[]>;
    getNodes(requestContext: ClientRequestContext, requestOptions: Paged<HierarchyRequestOptions<IModelDb>>, parentKey?: NodeKey): Promise<Node[]>;
    getNodesAndCount(requestContext: ClientRequestContext, requestOptions: Paged<HierarchyRequestOptions<IModelDb>>, parentKey?: NodeKey): Promise<{
        nodes: Node[];
        count: number;
    }>;
    getNodesCount(requestContext: ClientRequestContext, requestOptions: HierarchyRequestOptions<IModelDb>, parentKey?: NodeKey): Promise<number>;
    // @alpha
    getPagedDistinctValues(requestContext: ClientRequestContext, requestOptions: DistinctValuesRequestOptions<IModelDb, Descriptor, KeySet>): Promise<PagedResponse<DisplayValueGroup>>;
    // @internal (undocumented)
    getRulesetId(rulesetOrId: Ruleset | string): string;
    getSelectionScopes(requestContext: ClientRequestContext, requestOptions: SelectionScopeRequestOptions<IModelDb>): Promise<SelectionScope[]>;
    // @alpha
    loadHierarchy(requestContext: ClientRequestContext, requestOptions: HierarchyRequestOptions<IModelDb>): Promise<void>;
    get props(): PresentationManagerProps;
    rulesets(): RulesetManager;
    vars(rulesetId: string): RulesetVariablesManager;
}

// @public
export enum PresentationManagerMode {
    ReadOnly = 0,
    ReadWrite = 1
}

// @public
export interface PresentationManagerProps {
    activeLocale?: string;
    // @alpha
    activeUnitSystem?: PresentationUnitSystem;
    // @internal (undocumented)
    addon?: NativePlatformDefinition;
    // @internal
    cacheDirectory?: string;
    enableSchemasPreload?: boolean;
    // @internal (undocumented)
    eventSink?: EventSink;
    // @internal
    id?: string;
    localeDirectories?: string[];
    mode?: PresentationManagerMode;
    presentationAssetsRoot?: string;
    rulesetDirectories?: string[];
    supplementalRulesetDirectories?: string[];
    taskAllocationsMap?: {
        [priority: number]: number;
    };
    // @alpha
    updatesPollInterval?: number;
}

// @public
export type PresentationProps = PresentationPropsDeprecated | PresentationPropsNew;

// @public @deprecated (undocumented)
export interface PresentationPropsDeprecated extends PresentationManagerProps {
    // @internal
    clientManagerFactory?: (clientId: string, props: PresentationManagerProps) => PresentationManager;
    requestTimeout?: number;
    unusedClientLifetime?: number;
}

// @public (undocumented)
export interface PresentationPropsNew extends PresentationManagerProps {
    requestTimeout?: number;
    // @internal
    useSingleManager?: boolean;
}

// @beta
export class RulesetEmbedder {
    constructor(props: RulesetEmbedderProps);
    getRulesets(): Promise<Ruleset[]>;
    insertRuleset(ruleset: Ruleset, duplicateHandlingStrategy?: DuplicateRulesetHandlingStrategy): Promise<Id64String>;
    }

// @public
export interface RulesetEmbedderProps {
    imodel: IModelDb;
}

// @public
export interface RulesetManager {
    add(ruleset: Ruleset): RegisteredRuleset;
    clear(): void;
    get(id: string): RegisteredRuleset | undefined;
    remove(ruleset: RegisteredRuleset | [string, string]): boolean;
}

// @public
export interface RulesetVariablesManager {
    getBool(variableId: string): boolean;
    getId64(variableId: string): Id64String;
    getId64s(variableId: string): Id64String[];
    getInt(variableId: string): number;
    getInts(variableId: string): number[];
    getString(variableId: string): string;
    getValue(variableId: string, type: VariableValueTypes): VariableValue;
    setBool(variableId: string, value: boolean): void;
    setId64(variableId: string, value: Id64String): void;
    setId64s(variableId: string, value: Id64String[]): void;
    setInt(variableId: string, value: number): void;
    setInts(variableId: string, value: number[]): void;
    setString(variableId: string, value: string): void;
    setValue(variableId: string, type: VariableValueTypes, value: VariableValue): void;
}


// (No @packageDocumentation comment for this package)

```
