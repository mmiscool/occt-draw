hdebug                         : hdebug
hfill                          : hfill name proj [nbIso]
hhide                          : hhide
hload                          : hload outliner
hlrin2d                        : hlrin2d res shape proj_X proj_Y proj_Z eye_x eye_y eye_z
hlrin3d                        : hlrin3d res shape proj_X proj_Y proj_Z
hnullify                       : hnullify
houtl                          : houtl name shape
hprj                           : hprj name [view-id = 1]
hremove                        : hremove [name]
hres2d                         : hres2d
hsetprj                        : hsetprj [name]
hshowall                       : hshowall
hsin                           : hsin name outliner
hsout                          : hsout name outliner
hupdate                        : hupdate
reflectlines                   : reflectlines res shape proj_X proj_Y proj_Z
diffimage                      : diffimage imageFile1 imageFile2 [diffImageFile]
                               :           [-toleranceOfColor {0..1}=0] [-blackWhite {on|off}=off] [-borderFilter {on|off}=off]
                               :           [-display viewName prsName1 prsName2 prsNameDiff] [-exitOnClose] [-closeOnEscape]
                               : Compare two images by content and generate difference image.
                               : When -exitOnClose is specified, closing the view will exit application.
                               : When -closeOnEscape is specified, view will be closed on pressing Escape.
text2brep                      : text2brep name text"
                               :           [-pos X=0 Y=0 Z=0]"
                               :           [-halign {left|center|right}=left]"
                               :           [-valign {top|center|bottom|topfirstline}=bottom}]"
                               :           [-height height=16]"
                               :           [-aspect {regular|bold|italic|boldItalic}=regular]"
                               :           [-font font=Courier] [-strict {strict|aliases|any}=any]"
                               :           [-composite {on|off}=off]"
                               :           [-plane NormX NormY NormZ DirX DirY DirZ]",
v2dmode                        : v2dmode [-name viewName] [-mode {-on|-off}=-on]
                               :   name - name of existing view, if not defined, the active view is changed;
                               :   mode - switches On/Off rotation mode.
                               : Set 2D mode of the active viewer manipulating. The following mouse and key actions are disabled:
                               :  - rotation of the view by 3rd mouse button with Ctrl active
                               :  - set view projection using key buttons: A/D/T/B/L/R for AXO, Reset, Top, Bottom, Left, Right
                               : View camera position might be changed only by commands.
vactivate                      : vactivate view_id [-noUpdate]
                               : Activates view(viewer window) defined by its view_id.
vaddconnected                  : vaddconnected assembly_name object_name
                               : Adds object to assembly.
vangleparam                    : vangleparam name [-type interior|exterior]
                               :             [-showarrow first|second|both|none]
                               : Sets parameters for angle dimension.
                               : See also: vdimparam, vdimension.
vanim                          : List existing animations:
                               :   vanim
                               : 
                               : Animation playback:
                               :   vanim name {-play|-resume|-pause|-stop} [playFrom [playDuration]]
                               :              [-speed Coeff] [-freeLook] [-noPauseOnClick] [-lockLoop]
                               : 
                               :   -speed    playback speed (1.0 is normal speed)
                               :   -freeLook skip camera animations
                               :   -noPauseOnClick do not pause animation on mouse click
                               :   -lockLoop disable any interactions
                               : 
                               : Animation definition:
                               :   vanim Name/sub/name [-clear] [-delete]
                               :         [-start TimeSec] [-duration TimeSec] [-end TimeSec]
                               : 
                               : Animation name defined in path-style (anim/name or anim.name)
                               : specifies nested animations.
                               : There is no syntax to explicitly add new animation,
                               : and all non-existing animations within the name will be
                               : implicitly created on first use (including parents).
                               : 
                               : Each animation might define the SINGLE action (see below),
                               : like camera transition, object transformation or custom callback.
                               : Child animations can be used for defining concurrent actions.
                               : 
                               : Camera animation:
                               :   vanim name -view [-eye1 X Y Z] [-eye2 X Y Z]
                               :                    [-at1  X Y Z] [-at2  X Y Z]
                               :                    [-up1  X Y Z] [-up2  X Y Z]
                               :                    [-scale1 Scale] [-scale2 Scale]
                               :   -eyeX   camera Eye positions pair (start and end)
                               :   -atX    camera Center positions pair
                               :   -upX    camera Up directions pair
                               :   -scaleX camera Scale factors pair
                               : 
                               : Object animation:
                               :   vanim name -object [-loc1 X Y Z] [-loc2 X Y Z]
                               :                      [-rot1 QX QY QZ QW] [-rot2 QX QY QZ QW]
                               :                      [-scale1 Scale] [-scale2 Scale]
                               :  -locX   object Location points pair (translation)
                               :  -rotX   object Orientations pair (quaternions)
                               :  -scaleX object Scale factors pair (quaternions)
                               : 
                               : Custom callback:
                               :   vanim name -invoke "Command Arg1 Arg2 %Pts %LocalPts %Normalized ArgN"
                               : 
                               :   %Pts        overall animation presentation timestamp
                               :   %LocalPts   local animation timestamp
                               :   %Normalized local animation normalized value in range 0..1
                               : 
                               : Video recording:
                               :   vanim name -record FileName [Width Height] [-fps FrameRate=24]
                               :         [-format Format] [-vcodec Codec] [-pix_fmt PixelFormat]
                               :         [-crf Value] [-preset Preset]
                               :   -fps     video framerate
                               :   -format  file format, container (matroska, etc.)
                               :   -vcodec  video codec identifier (ffv1, mjpeg, etc.)
                               :   -pix_fmt image pixel format (yuv420p, rgb24, etc.)
                               :   -crf     constant rate factor (specific to codec)
                               :   -preset  codec parameters preset (specific to codec)
vanimation                     : Alias for vanim
vaspects                       : vaspects [-noupdate|-update] [name1 [name2 [...]] | -defaults] [-subshapes subname1 [subname2 [...]]]
                               :          [-visibility {0|1}]
                               :          [-color {ColorName | R G B}] [-unsetColor]
                               :          [-backfaceColor Color]
                               :          [-material MatName] [-unsetMaterial]
                               :          [-transparency Transp] [-unsetTransparency]
                               :          [-width LineWidth] [-unsetWidth]
                               :          [-lineType {solid|dash|dot|dotDash|0xHexPattern} [-stippleFactor factor]]
                               :            [-unsetLineType]
                               :          [-markerType {.|+|x|O|xcircle|pointcircle|ring1|ring2|ring3|ball|ImagePath}]
                               :            [-unsetMarkerType]
                               :          [-markerSize Scale] [-unsetMarkerSize]
                               :          [-freeBoundary {0|1}]
                               :            [-freeBoundaryWidth Width] [-unsetFreeBoundaryWidth]
                               :            [-freeBoundaryColor {ColorName | R G B}] [-unsetFreeBoundaryColor]
                               :          [-isoOnTriangulation 0|1]
                               :          [-maxParamValue {value}]
                               :          [-sensitivity {selection_mode} {value}]
                               :          [-shadingModel {unlit|flat|gouraud|phong|pbr|pbr_facet}]
                               :            [-unsetShadingModel]
                               :          [-interior {solid|hatch|hidenline|point}] [-setHatch HatchStyle]
                               :            [-unsetInterior]
                               :          [-faceBoundaryDraw {0|1}] [-mostContinuity {c0|g1|c1|g2|c2|c3|cn}]
                               :          [-faceBoundaryWidth LineWidth] [-faceBoundaryColor R G B] [-faceBoundaryType LineType]
                               :          [-drawEdges {0|1}] [-edgeType LineType] [-edgeColor R G B] [-quadEdges {0|1}]
                               :          [-drawSilhouette {0|1}]
                               :          [-alphaMode {opaque|mask|blend|maskblend|blendauto} [alphaCutOff=0.5]]
                               :          [-dumpJson] [-dumpCompact {0|1}] [-dumpDepth depth]
                               : Manage presentation properties of all, selected or named objects.
                               : When -subshapes is specified than following properties will be assigned to specified sub-shapes.
                               : When -defaults is specified than presentation properties will be
                               : assigned to all objects that have not their own specified properties
                               : and to all objects to be displayed in the future.
                               : If -defaults is used there should not be any objects' names nor -subshapes specifier.
                               : See also vlistcolors and vlistmaterials to list named colors and materials
                               : accepted by arguments -material and -color
vautozfit                      : vautozfit [on={1|0}] [scale]
                               : Prints or changes parameters of automatic z-fit mode:
                               :  "on" - turns automatic z-fit on or off;
                               :  "scale" - specifies factor to scale computed z range.
vaxis                          : vaxis name [Xa] [Ya] [Za] [Xb] [Yb] [Zb]
                               : Creates an axis. If  the values are not defined,
                               : an axis is created by interactive selection of two vertices or one edge.
vaxisortho                     : vaxisortho name
                               : Creates an axis by interactive selection of an edge and a vertex.
                               : The axis will be orthogonal to the selected edge.
vaxispara                      : vaxispara name
                               : Creates an axis by interactive selection of an edge and a vertex.
vaxo                           : vaxo or <A> : Display axonometric view (+X-Y+Z) in the 3D viewer window.
vback                          : vback : Display back view (-X+Z) in the 3D viewer window.
vbackground                    : vbackground [-color Color [-default]]
                               :     [-gradient Color1 Color2 [-default]
                               :     [-gradientMode {NONE|HORIZONTAL|VERTICAL|DIAG1|DIAG2|CORNER1|CORNER2|CORNER3|ELLIPTICAL}]=VERT]
                               :     [-imageFile ImageFile [-imageMode {CENTERED|TILED|STRETCH|NONE}]=CENTERED [-srgb {0|1}]=1]
                               :     [-cubemap CubemapFile1 [CubeMapFiles2-5] [-order TilesIndexes1-6] [-invertedz]=0]
                               :     [-pbrEnv {ibl|noibl|keep}]
                               : Changes background or some background settings.
                               :  -color        sets background color
                               :  -gradient     sets background gradient starting and ending colors
                               :  -gradientMode sets gradient fill method
                               :  -default      sets background default gradient or color
                               :  -imageFile    sets filename of image used as background
                               :  -imageMode    sets image fill type
                               :  -cubemap      sets environment cubemap as background
                               :  -invertedz    sets inversion of Z axis for background cubemap rendering; FALSE when unspecified
                               :  -pbrEnv       sets on/off Image Based Lighting (IBL) from background cubemap for PBR
                               :  -srgb         prefer sRGB texture format when applicable; TRUE when unspecified"
                               :  -order        defines order of tiles in one image cubemap
                               :                TileIndexi defubes an index in range [0, 5] for i tile of one image packed cubemap
                               :                (has no effect in case of multi-image cubemaps).
vbottom                        : vbottom : Display bottom view (+X-Y) in the 3D viewer window.
vbounding                      : vbounding [-noupdate|-update] [-mode] name1 [name2 [...]]
                               :           [-print] [-hide]
                               : Temporarily display bounding box of specified Interactive Objects,
                               : or print it to console if -print is specified.
                               : Already displayed box might be hidden by -hide option.
vbsdf                          : vbsdf [name] [options]
                               : nAdjusts parameters of material BSDF:
                               :  -help    shows this message
                               :  -print   print BSDF
                               :  -kd      weight of the Lambertian BRDF
                               :  -kr      weight of the reflection BRDF
                               :  -kt      weight of the transmission BTDF
                               :  -ks      weight of the glossy Blinn BRDF
                               :  -le      self-emitted radiance
                               :  -fresnel Fresnel coefficients; Allowed fresnel formats are: Constant x,
                               :           Schlick x y z, Dielectric x, Conductor x y
                               :  -roughness   roughness of material (Blinn's exponent)
                               :  -absorpcoeff absorption coefficient (only for transparent material)
                               :  -absorpcolor absorption color (only for transparent material)
                               :  -normalize   normalize BSDF coefficients
vcamera                        : vcamera [PrsName] [-ortho] [-projtype]
                               :         [-persp]
                               :         [-fovy   [Angle]] [-distance [Distance]]
                               :         [-stereo] [-leftEye] [-rightEye]
                               :         [-iod [Distance]] [-iodType    [absolute|relative]]
                               :         [-zfocus [Value]] [-zfocusType [absolute|relative]]
                               :         [-fov2d  [Angle]] [-lockZup {0|1}]
                               :         [-rotationMode {active|pick|pickCenter|cameraAt|scene}]
                               :         [-navigationMode {orbit|walk|flight}]
                               :         [-xrPose base|head=base]
                               : Manages camera parameters.
                               : Displays frustum when presentation name PrsName is specified.
                               : Prints current value when option called without argument.
                               : 
                               : Orthographic camera:
                               :  -ortho      activate orthographic projection.
                               : 
                               : Perspective camera:
                               :  -persp      activate perspective  projection (mono);
                               :  -fovy       field of view in y axis, in degrees;
                               :  -fov2d      field of view limit for 2d on-screen elements;
                               :  -distance   distance of eye from camera center;
                               :  -lockZup    lock Z up (turntable mode);
                               :  -rotationMode rotation mode (gravity point);
                               :  -navigationMode navigation mode.
                               : 
                               : Stereoscopic camera:
                               :  -stereo     perspective  projection (stereo);
                               :  -leftEye    perspective  projection (left  eye);
                               :  -rightEye   perspective  projection (right eye);
                               :  -iod        intraocular distance value;
                               :  -iodType    distance type, absolute or relative;
                               :  -zfocus     stereographic focus value;
                               :  -zfocusType focus type, absolute or relative.
vchangeplane                   : vchangeplane plane_name
                               :              [x=center_x y=center_y z=center_z]
                               :              [dx=dir_x dy=dir_y dz=dir_z]
                               :              [sx=size_x sy=size_y]
                               :              [minsize=value]
                               :              [noupdate]
                               : Changes parameters of the plane:
                               :  - x y z     - center
                               :  - dx dy dz  - normal
                               :  - sx sy     - plane sizes
                               :  - noupdate  - do not update/redisplay the plane in context
                               : Please enter coordinates in format "param=value" in arbitrary order.
vchangeselected                : vchangeselected shape : Add shape to selection or remove one from it.
vchild                         : vchild parent [-add] [-remove] [-ignoreParentTrsf {0|1}] child1 [child2] [...]
                               : Command for testing low-level presentation connections.
                               : vconnect command should be used instead.
vcircle                        : vcircle CircleName [PointName PointName PointName IsFilled]
                               :                    [PlaneName PointName Radius IsFilled]
                               : Creates a circle from named or interactively selected entities.
                               : Parameter IsFilled is defined as 0 or 1.
vclear                         : vclear : Remove all the object from the viewer
vclipplane                     : vclipplane planeName [{0|1}]
                               :     [-equation1 A B C D]
                               :     [-equation2 A B C D]
                               :     [-boxInterior MinX MinY MinZ MaxX MaxY MaxZ]
                               :     [-set|-unset|-setOverrideGlobal [objects|views]]
                               :     [-maxPlanes]
                               :     [-capping {0|1}]
                               :       [-color R G B] [-transparency Value] [-hatch {on|off|ID}]
                               :       [-texName Texture] [-texScale SX SY] [-texOrigin TX TY]
                               :         [-texRotate Angle]
                               :       [-useObjMaterial {0|1}] [-useObjTexture {0|1}]
                               :         [-useObjShader {0|1}]
                               : 
                               : Clipping planes management:
                               :  -maxPlanes   print plane limit for view;
                               :  -delete      delete plane with given name;
                               :  {off|on|0|1} turn clipping on/off;
                               :  -set|-unset  set/unset plane for Object or View list;
                               :               applied to active View when list is omitted;
                               :  -equation A B C D change plane equation;
                               :  -clone SourcePlane NewPlane clone the plane definition.
                               : 
                               : Capping options:
                               :  -capping {off|on|0|1} turn capping on/off;
                               :  -color R G B          set capping color;
                               :  -transparency Value   set capping transparency 0..1;
                               :  -texName Texture      set capping texture;
                               :  -texScale SX SY       set capping tex scale;
                               :  -texOrigin TX TY      set capping tex origin;
                               :  -texRotate Angle      set capping tex rotation;
                               :  -hatch {on|off|ID}    set capping hatching mask;
                               :  -useObjMaterial {off|on|0|1} use material of clipped object;
                               :  -useObjTexture  {off|on|0|1} use texture of clipped object;
                               :  -useObjShader   {off|on|0|1} use shader program of object.
vclose                         : vclose [view_id [keep_context=0|1]]
                               : or vclose ALL - to remove all created views
                               :  - removes view(viewer window) defined by its view_id.
                               :  - keep_context: by default 0; if 1 and the last view is deleted the current context is not removed.
vcolorconvert                  : vcolorconvert {from|to} type C1 C2 C2
                               : vcolorconvert from type C1 C2 C2 : Converts color from specified color space to linear RGB
                               : vcolorconvert to   type R  G  B  : Converts linear RGB color to specified color space
                               : Type can be sRGB, HLS, Lab, or Lch.
vcolordiff                     : vcolordiff R1 G1 B1 R2 G2 B2 : returns CIEDE2000 color difference between two RGB colors.
vcolorscale                    : vcolorscale name [-noupdate|-update] [-demo]
                               :       [-range RangeMin=0 RangeMax=1 NbIntervals=10]
                               :       [-font HeightFont=20]
                               :       [-logarithmic {on|off}=off] [-reversed {on|off}=off]
                               :       [-smoothTransition {on|off}=off]
                               :       [-hueRange MinAngle=230 MaxAngle=0]
                               :       [-colorRange MinColor=BLUE1 MaxColor=RED]
                               :       [-textPos {left|right|center|none}=right]
                               :       [-labelAtBorder {on|off}=on]
                               :       [-colors Color1 Color2 ...] [-color Index Color]
                               :       [-labels Label1 Label2 ...] [-label Index Label]
                               :       [-freeLabels NbOfLabels Label1 Label2 ...]
                               :       [-xy Left=0 Bottom=0]
                               :       [-uniform lightness hue_from hue_to]
                               :  -demo       display a color scale with demonstration values
                               :  -colors     set colors for all intervals
                               :  -color      set color for specific interval
                               :  -uniform    generate colors with the same lightness
                               :  -textpos    horizontal label position relative to color scale bar
                               :  -labelAtBorder vertical label position relative to color interval;
                               :              at border means the value inbetween neighbor intervals,
                               :              at center means the center value within current interval
                               :  -labels     set labels for all intervals
                               :  -freeLabels same as -labels but does not require
                               :              matching the number of intervals
                               :  -label      set label for specific interval
                               :  -title      set title
                               :  -reversed   setup smooth color transition between intervals
                               :  -smoothTransition swap colorscale direction
                               :  -hueRange   set hue angles corresponding to minimum and maximum values
vcomputehlr                    : vcomputehlr shapeInput hlrResult [-algoType {algo|polyAlgo}=polyAlgo]
                               :     [eyeX eyeY eyeZ dirX dirY dirZ upX upY upZ]
                               :     [-showTangentEdges {on|off}=off] [-nbIsolines N=0] [-showHiddenEdges {on|off}=off]
                               : Arguments:
                               :   shapeInput - name of the initial shape
                               :   hlrResult  - result HLR object from initial shape
                               :   eye, dir are eye position and look direction
                               :   up is the look up direction vector
                               :  -algoType HLR algorithm to use
                               :  -showTangentEdges include tangent edges
                               :  -nbIsolines include isolines
                               :  -showHiddenEdges include hidden edges
                               : Use vtop to see projected HLR shape.
vconnect                       : vconnect name Xo Yo Zo object1 object2 ... [color=NAME]
                               : Creates and displays AIS_ConnectedInteractive object from input object and location.
vconnectto                     : vconnectto instance_name Xo Yo Zo object [-nodisplay|-noupdate|-update]
                               : Makes an instance 'instance_name' of 'object' with position (Xo Yo Zo).
                               :  -nodisplay - only creates interactive object, but not displays it.
vconvert                       : vconvert v [Mode={window|view}]
                               : vconvert x y [Mode={window|view|grid|ray}]
                               : vconvert x y z [Mode={window|grid}]
                               : Convert the given coordinates to window/view/model space:
                               :  - window - convert to window coordinates, pixels;
                               :  - view   - convert to view projection plane;
                               :  - grid   - convert to model coordinates, given on grid;
                               :  - ray    - convert projection ray to model coordinates.
vcylinder                      : vcylinder name [R1 R2 Height] [-height H] [-radius R] [-bottomRadius R1 -topRadius R2]
                               :                [-nbSlices Number=100] [-noupdate]
                               : Creates and displays a cylinder.
                               : Parameters of the cylinder:
                               :  - R1     cylinder bottom radius
                               :  - R2     cylinder top radius
                               :  - Height cylinder height
vdefaults                      : vdefaults [-absDefl value] [-devCoeff value] [-angDefl value]
                               :           [-autoTriang {off/on | 0/1}]
vdimension                     : vdimension name {-angle|-length|-radius|-diameter}
                               :     [-shapes shape1 [shape2 [shape3]]
                               :     [-selected]
                               :     [-text 3d|2d wf|sh|wireframe|shading IntegerSize]
                               :     [-font FontName]
                               :     [-label left|right|hcenter|hfit top|bottom|vcenter|vfit]
                               :     [-arrow external|internal|fit]
                               :     [-zoomablearrow]
                               :     [{-arrowlength|-arlen} RealArrowLength]
                               :     [{-arrowangle|-arangle} ArrowAngle(degrees)]
                               :     [-plane xoy|yoz|zox]
                               :     [-flyout FloatValue -extension FloatValue]
                               :     [-autovalue]
                               :     [-value CustomRealValue]
                               :     [-textvalue CustomTextValue]
                               :     [-dispunits DisplayUnitsString]
                               :     [-modelunits ModelUnitsString]
                               :     [-showunits | -hideunits]
                               : Builds angle, length, radius and diameter dimensions.
                               : See also: vdimparam, vmovedim.
vdimparam                      : vdimparam name
                               :     [-text 3d|2d wf|sh|wireframe|shading IntegerSize]
                               :     [-font FontName]
                               :     [-label left|right|hcenter|hfit top|bottom|vcenter|vfit]
                               :     [-arrow external|internal|fit]
                               :     [-zoomablearrow 0|1]
                               :     [{-arrowlength|-arlen} RealArrowLength]
                               :     [{-arrowangle|-arangle} ArrowAngle(degrees)]
                               :     [-plane xoy|yoz|zox]
                               :     [-flyout FloatValue -extension FloatValue]
                               :     [-value CustomNumberValue]
                               :     [-textvalue CustomTextValue]
                               :     [-dispunits DisplayUnitsString]
                               :     [-modelunits ModelUnitsString]
                               :     [-showunits | -hideunits]
                               : Sets parameters for angle, length, radius and diameter dimensions.
                               : See also: vmovedim, vdimension.
vdir                           : vdir [mask] [-list]
                               : Lists all objects displayed in 3D viewer
                               :   mask - name filter like prefix*
                               :  -list - format list with new-line per name; OFF by default
vdisconnect                    : vdisconnect assembly_name {object_name|object_number|'all'}
                               : Disconnects all objects from assembly or disconnects object by name or number.
                               : Use vlistconnected to enumerate assembly children.
vdisplay                       : vdisplay [-noupdate|-update] [-mutable] [-neutral]
                               :          [-trsfPers {zoom|rotate|zoomRotate|none}=none]
                               :             [-trsfPersPos X Y [Z]] [-3d]
                               :             [-2d|-trihedron [{top|bottom|left|right|topLeft
                               :                             |topRight|bottomLeft|bottomRight}
                               :               [offsetX offsetY]]]
                               :          [-dispMode mode] [-highMode mode]
                               :          [-layer index] [-top|-topmost|-overlay|-underlay]
                               :          [-redisplay] [-erased]
                               :          [-noecho] [-autoTriangulation {0|1}]
                               :          name1 [name2] ... [name n]
                               : Displays named objects.
                               :  -noupdate    Suppresses viewer redraw call.
                               :  -mutable     Enables optimizations for mutable objects.
                               :  -neutral     Draws objects in main viewer.
                               :  -erased      Loads the object into context, but does not display it.
                               :  -layer       Sets z-layer for objects.
                               :               Alternatively -overlay|-underlay|-top|-topmost
                               :               options can be used for the default z-layers.
                               :  -top         Draws object on top of main presentations
                               :               but below topmost.
                               :  -topmost     Draws in overlay for 3D presentations.
                               :               with independent Depth.
                               :  -overlay     Draws objects in overlay for 2D presentations.
                               :               (On-Screen-Display)
                               :  -underlay    Draws objects in underlay for 2D presentations.
                               :               (On-Screen-Display)
                               :  -selectable|-noselect Controls selection of objects.
                               :  -trsfPers    Sets a transform persistence flags.
                               :  -trsfPersPos Sets an anchor point for transform persistence.
                               :  -2d          Displays object in screen coordinates.
                               :               (DY looks up)
                               :  -dispmode    Sets display mode for objects.
                               :  -highmode    Sets hilight mode for objects.
                               :  -redisplay   Recomputes presentation of objects.
                               :  -noecho      Avoid printing of command results.
                               :  -autoTriang  Enable/disable auto-triangulation for displayed shape.
vdisplayall                    : vdisplayall : Displays all erased interactive objects (see vdir and vstate).
vdisplaytype                   : vdisplaytype <Type> <Signature>
                               : Display all the objects of one given kind (see vtypes) which are stored the interactive context.
                               : The following types are possible:
                               :   Point, Axis, Trihedron, PlaneTrihedron, Line, Circle, Plane, Shape,
                               :   ConnectedShape, MultiConn.Shape, ConnectedInter., MultiConn., Constraint and Dimension.
vdonly                         : vdonly [-noupdate|-update] [name1] ...  [name n]
                               : Displays only selected or named objects.
vdrawparray                    : vdrawparray name TypeOfArray={points|segments|polylines|triangles
                               :                    |trianglefans|trianglestrips|quads|quadstrips|polygons}
                               :             [-deinterleaved|-mutable]
                               :             [vertex={'v' x y z [normal={'n' nx ny nz}] [color={'c' r g b}] [texel={'t' tx ty}]]
                               :             [bound= {'b' nbVertices [bound_color={'c' r g b}]]
                               :             [edge=  {'e' vertexId]
                               :             [-shape shapeName] [-patch]
                               : Commands create an Interactive Object for specified Primitive Array definition
                               : with the main purpose is covering various combinations by tests.
vdrawsphere                    : vdrawsphere shapeName Fineness [X=0.0 Y=0.0 Z=0.0] [Radius=100.0] [ToShowEdges=0] [ToPrintInfo=1]
vdrawtext                      : vdrawtext name text
                               :           [-pos X Y Z]={0 0 0}
                               :           [-color {R G B|name}]=yellow
                               :           [-halign {left|center|right}]=left
                               :           [-valign {top|center|bottom|topfirstline}}]=bottom
                               :           [-angle angle]=0
                               :           [-zoom {0|1}]=0
                               :           [-height height]=16
                               :           [-wrapping width]=40
                               :           [-aspect {regular|bold|italic|boldItalic}]=regular
                               :           [-font font]=Times
                               :           [-2d] [-perspos {X Y Z}]={0 0 0}
                               :           [-disptype {blend|decal|shadow|subtitle|dimension|normal}}=normal
                               :           [-subcolor {R G B|name}]=white
                               :           [-noupdate]
                               :           [-plane NormX NormY NormZ DirX DirY DirZ]
                               :           [-flipping] [-ownanchor {0|1}]=1
                               : Display text label at specified position.
                               : Within -perspos, X and Y define the coordinate origin in 2d space relative to the view window.
                               : Example: X=0 Y=0 is center, X=1 Y=1 is upper right corner etc...
                               : Z coordinate defines the gap from border of view window (except center position).
vdriver                        : vdriver [-list] [-default DriverName] [-load DriverName]
                               : Manages active graphic driver factory.
                               : Prints current active driver when called without arguments.
                               : Makes specified driver active when ActiveName argument is specified.
                               :  -list    print registered factories
                               :  -default define which factory should be used by default (to be used by next vinit call)
                               :  -load    try loading factory plugin and set it as default one
vdump                          : vdump <filename>.png [-width Width -height Height]
                               :       [-buffer rgb|rgba|depth=rgb]
                               :       [-stereo mono|left|right|blend|sideBySide|overUnder=mono]
                               :       [-xrPose base|head|handLeft|handRight=base]
                               :       [-tileSize Size=0]
                               : Dumps content of the active view into image file.
verase                         : verase [-noupdate|-update] [name1] ...  [name n] [-noerror]
                               : Erases selected or named objects.
                               : If there are no selected or named objects the whole viewer is erased.
                               : Option -noerror prevents exception on non-existing objects.
veraseall                      : veraseall : Erases all objects displayed in the viewer.
verasetype                     : verasetype <Type>
                               : Erase all the displayed objects of one given kind (see vtypes).
                               : The following types are possible:
                               :   Point, Axis, Trihedron, PlaneTrihedron, Line, Circle, Plane, Shape,
                               :   ConnectedShape, MultiConn.Shape, ConnectedInter., MultiConn., Constraint and Dimension.
vfit                           : vfit or <F> [-selected] [-noupdate]
                               : Fit all / selected. Objects in the view are visualized to occupy the maximum surface.
vfitarea                       : vfitarea [x1 y1 x2 y2] [x1 y1 z1 x2 y2 z2]
                               : Fit view to show area located between two points
                               : given in world 2D or 3D coordinates.
vfont                          : vfont [-add pathToFont [fontName] [regular,bold,italic,boldItalic=undefined] [singleStroke]]
                               :       [-strict {any|aliases|strict}] [-find fontName [regular,bold,italic,boldItalic=undefined]]
                               :       [-verbose {on|off}]
                               :       [-findAll fontNameMask] [-findInfo fontName]
                               :       [-unicodeFallback {on|off}]
                               :       [-clear] [-init] [-list] [-names]
                               :       [-aliases [aliasName]] [-addAlias Alias FontName] [-removeAlias Alias FontName]
                               :       [-clearAlias Alias] [-clearAliases]
                               : Work with font registry - register font, list available fonts, find font.
                               :  -findAll  is same as -find, but can print more than one font when mask is passed.
                               :  -findInfo is same as -find, but prints complete font information instead of family name.
vfps                           : vfps [framesNb=100] [-duration seconds] : estimate average frame rate for active view.
vfront                         : vfront : Display front view (+X+Z) in the 3D viewer window.
vgenenvlut                     : vgenenvlut [-size size = 128] [-nbsamples nbsamples = 1024]
                               : Generates PBR environment look up table.
                               : Saves it as C++ source file which is expected to be included in code.
                               : The path where result will be located is 'Graphic3d_TextureRoot::TexturesFolder()'.
                               :  -size size of one side of resulted square table
                               :  -nbsamples number of samples used in Monte-Carlo integration
vglinfo                        : vglinfo [-short|-basic|-complete] [-lineWidth Value=80]
                               :         [GL_VENDOR] [GL_RENDERER] [GL_VERSION]
                               :         [GL_SHADING_LANGUAGE_VERSION] [GL_EXTENSIONS]
                               : Print OpenGL info.
                               :  -lineWidth split values longer than specified value into multiple lines;
                               :             -1 disables splitting.
vgraduatedtrihedron            : vgraduatedtrihedron : -on/-off [-xname Name] [-yname Name] [-zname Name] [-arrowlength Value]
                               :     [-namefont Name] [-valuesfont Name]
                               :     [-xdrawname on/off] [-ydrawname on/off] [-zdrawname on/off]
                               :     [-xnameoffset IntVal] [-ynameoffset IntVal] [-znameoffset IntVal]
                               :     [-xnamecolor Color] [-ynamecolor Color] [-znamecolor Color]
                               :     [-xdrawvalues on/off] [-ydrawvalues on/off] [-zdrawvalues on/off]
                               :     [-xvaluesoffset IntVal] [-yvaluesoffset IntVal] [-zvaluesoffset IntVal]
                               :     [-xcolor Color] [-ycolor Color] [-zcolor Color]
                               :     [-xdrawticks on/off] [-ydrawticks on/off] [-zdrawticks on/off]
                               :     [-xticks Number] [-yticks Number] [-zticks Number]
                               :     [-xticklength IntVal] [-yticklength IntVal] [-zticklength IntVal]
                               :     [-drawgrid on/off] [-drawaxes on/off]
                               : Display or erase graduated trihedron
                               :  - xname, yname, zname - names of axes, default: X, Y, Z
                               :  - namefont - font of axes names. Default: Arial
                               :  - xnameoffset, ynameoffset, znameoffset - offset of name
                               :    from values or tickmarks or axis. Default: 30
                               :  - xnamecolor, ynamecolor, znamecolor - colors of axes names
                               :  - xvaluesoffset, yvaluesoffset, zvaluesoffset - offset of values
                               :    from tickmarks or axis. Default: 10
                               :  - valuesfont - font of axes values. Default: Arial
                               :  - xcolor, ycolor, zcolor - color of axis and values
                               :  - xticks, yticks, xzicks - number of tickmark on axes. Default: 5
                               :  - xticklength, yticklength, xzicklength - length of tickmark on axes. Default: 10
vgrid                          : vgrid [off] [-type {rect|circ}] [-mode {line|point}] [-origin X Y] [-rotAngle Angle] [-zoffset DZ]
                               :       [-step X Y] [-size DX DY]
                               :       [-step StepRadius NbDivisions] [-radius Radius]
vhelp                          : vhelp : display help on the viewer commands and list of hotkeys.
vhighlightselected             : vhighlightselected [0|1] : alias for vselprops -highlightSelected.
vhlr                           : vhlr {on|off} [-showHidden={1|0}] [-algoType={algo|polyAlgo}] [-noupdate]
                               : Hidden Line Removal algorithm.
                               :  -showHidden if set ON, hidden lines are drawn as dotted ones;
                               :  -algoType   type of HLR algorithm:
                               :             'algo' - exact HLR algorithm is applied;
                               :             'polyAlgo' - polygonal HLR algorithm is applied.
vhlrtype                       : vhlrtype {algo|polyAlgo} [shape_1 ... shape_n] [-noupdate]
                               : Changes the type of HLR algorithm using for shapes:
                               :  'algo' - exact HLR algorithm is applied;
                               :  'polyAlgo' - polygonal HLR algorithm is applied.
                               : If shapes are not given - option is applied to all shapes in the view.
vimmediatefront                : vimmediatefront : render immediate mode to front buffer or to back buffer
vinit                          : vinit [-name viewName] [-left leftPx] [-top topPx] [-width widthPx] [-height heightPx]
                               :       [-exitOnClose] [-closeOnEscape] [-cloneActive] [-virtual {on|off}=off] [-2d_mode {on|off}=off]
                               :       [-display displayName]
                               : Creates new View window with specified name viewName.
                               : By default the new view is created in the viewer and in graphic driver shared with active view.
                               :  -name {driverName/viewerName/viewName | viewerName/viewName | viewName}
                               :        if driverName isn't specified the driver will be shared with active view;
                               :        if viewerName isn't specified the viewer will be shared with active view.
                               :  -display HostName.DisplayNumber[:ScreenNumber]
                               : 
                               : Display name will be used within creation of graphic driver, when specified.
                               :  -left,  -top    pixel position of left top corner of the window.
                               :  -width, -height width and height of window respectively.
                               :  -cloneActive flag to copy camera and dimensions of active view.
                               :  -exitOnClose when specified, closing the view will exit application.
                               :  -closeOnEscape when specified, view will be closed on pressing Escape.
                               :  -virtual create an offscreen window within interactive session
                               :  -2d_mode when on, view will not react on rotate scene events
                               : Additional commands for operations with views: vclose, vactivate, vviewlist.
visos                          : visos [name1 ...] [nbUIsos nbVIsos IsoOnPlane(0|1)]
                               : If last 3 optional parameters are not set prints numbers of U-, V- isolines and IsoOnPlane.
vlayerline                     : vlayerline x1 y1 x2 y2 [linewidth=0.5] [linetype=0] [transparency=1.0]
vleft                          : vleft : Display left view (-Y+Z) in the 3D viewer window.
vlengthparam                   : vlengthparam name [-direction {ox|oy|oz|x y z|autodirection}]
                               : Sets parameters for length dimension.
                               : See also: vdimparam, vdimension.
vlight                         : vlight [lightName] [-noupdate]
                               :        [-clear|-defaults] [-layer Id] [-local|-global] [-disable|-enable]
                               :        [-type {ambient|directional|spotlight|positional}] [-name value]
                               :        [-position X Y Z] [-direction X Y Z] [-color colorName] [-intensity value]
                               :        [-headlight 0|1] [-castShadows 0|1]
                               :        [-range value] [-constAttenuation value] [-linearAttenuation value]
                               :        [-spotExponent value] [-spotAngle angleDeg]
                               :        [-smoothAngle value] [-smoothRadius value]
                               :        [-display] [-showName 1|0] [-showRange 1|0] [-prsZoomable 1|0] [-prsSize Value]
                               :        [-arcSize Value]
                               : 
                               : Command manages light sources. Without arguments shows list of lights.
                               : Arguments affecting the list of defined/active lights:
                               :  -clear       remove all light sources;
                               :  -defaults    defines two standard light sources;
                               :  -reset       resets light source parameters to default values;
                               :  -type        sets type of light source;
                               :  -name        sets new name to light source;
                               :  -global      assigns light source to all views (default state);
                               :  -local       assigns light source to active view;
                               :  -zlayer      assigns light source to specified Z-Layer.
                               : 
                               : Ambient light parameters:
                               :  -color       sets (normalized) light color;
                               :  -intensity   sets intensity of light source, 1.0 by default;
                               :               affects also environment cubemap intensity.
                               : 
                               : Point light parameters:
                               :  -color       sets (normalized) light color;
                               :  -intensity   sets PBR intensity;
                               :  -range       sets clamping distance;
                               :  -constAtten  (obsolete) sets constant attenuation factor;
                               :  -linearAtten (obsolete) sets linear   attenuation factor;
                               :  -smoothRadius sets PBR smoothing radius.
                               : 
                               : Directional light parameters:
                               :  -color       sets (normalized) light color;
                               :  -intensity   sets PBR intensity;
                               :  -direction   sets direction;
                               :  -headlight   sets headlight flag;
                               :  -castShadows enables/disables shadow casting;
                               :  -smoothAngle sets PBR smoothing angle (in degrees) within 0..90 range.
                               : 
                               : Spot light parameters:
                               :  -color       sets (normalized) light color;
                               :  -intensity   sets PBR intensity;
                               :  -range       sets clamping distance;
                               :  -position    sets position;
                               :  -direction   sets direction;
                               :  -spotAngle   sets spotlight angle;
                               :  -spotExp     sets spotlight exponenta;
                               :  -headlight   sets headlight flag;
                               :  -constAtten  (obsolete) sets constant attenuation factor;
                               :  -linearAtten (obsolete) sets linear   attenuation factor.
                               : 
                               : Light presentation parameters:
                               :  -display     adds light source presentation;
                               :  -showName    shows/hides the name of light source; 1 by default;
                               :  -showRange   shows/hides the range of spot/positional light source; 1 by default;
                               :  -prsZoomable makes light presentation zoomable/non-zoomable;
                               :  -prsDraggable makes light presentation draggable/non-draggable;
                               :  -prsSize     sets light presentation size;
                               :  -arcSize     sets arc presentation size(in pixels)
                               :               for rotation directional light source; 25 by default.
                               : 
                               : Examples:
                               :  vlight redlight -type POSITIONAL -headlight 1 -pos 0 1 1 -color RED
                               :  vlight redlight -delete
vline                          : vline LineName [Xa/PointName] [Ya/PointName] [Za] [Xb] [Yb] [Zb]
                               : Creates a line from coordinates, named or interactively selected vertices.
vlistcolors                    : vlistcolors [*] [ColorName1 [ColorName2 [...]]] [dump.html]
                               : Without arguments, command prints the list of standard colors.
                               : Otherwise, properties of specified colors will be printed
                               : or dumped into specified file.
                               : * can be used to refer to complete list of standard colors.
vlistconnected                 : vlistconnected assembly_name
                               : Lists objects in assembly.
vlistmaterials                 : vlistmaterials [*] [MaterialName1 [MaterialName2 [...]]] [dump.obj|dump.html]
                               : Without arguments, command prints the list of standard materials.
                               : Otherwise, properties of specified materials will be printed
                               : or dumped into specified file.
                               : * can be used to refer to complete list of standard materials.
vloadselection                 : vloadselection [-context] [name1] ... [nameN]
                               : Allows to load selection primitives for the shapes with names given without displaying them.
vlocation                      : vlocation name
                               :     [-reset] [-copyFrom otherName]
                               :     [-translate    X Y [Z]] [-rotate    x y z dx dy dz angle] [-scale    [X Y Z] scale]
                               :     [-pretranslate X Y [Z]] [-prerotate x y z dx dy dz angle] [-prescale [X Y Z] scale]
                               :     [-mirror x y z dx dy dz] [-premirror x y z dx dy dz]
                               :     [-setLocation X Y [Z]] [-setRotation QX QY QZ QW] [-setScale [X Y Z] scale]
                               : Object local transformation management:
                               :  -reset        resets transformation to identity
                               :  -translate    applies translation vector
                               :  -rotate       applies rotation around axis
                               :  -scale        applies scale factor with optional anchor
                               :  -mirror       applies mirror transformation
                               :  -pretranslate pre-multiplies translation vector
                               :  -prerotate    pre-multiplies rotation around axis
                               :  -prescale     pre-multiplies scale  transformation
                               :  -premirror    pre-multiplies mirror transformation
                               :  -setLocation  overrides translation part
                               :  -setRotation  overrides rotation part with specified quaternion
                               :  -setScale     overrides scale factor
vmanipulator                   : vmanipulator Name [-attach AISObject | -detach | ...]
                               : Tool to create and manage AIS manipulators.
                               : Options:
                               :  '-attach AISObject'                 attach manipulator to AISObject
                               :  '-adjustPosition {0|center|location|shapeLocation}' adjust position when attaching
                               :  '-adjustSize     {0|1}'             adjust size when attaching
                               :  '-enableModes    {0|1}'             enable modes when attaching
                               :  '-view  {active | [name of view]}'  display manipulator only in defined view,
                               :                                      by default it is displayed in all views of the current viewer
                               :  '-detach'                           detach manipulator
                               :  '-startTransform mouse_x mouse_y' - invoke start of transformation
                               :  '-transform      mouse_x mouse_y' - invoke transformation
                               :  '-stopTransform  [abort]'         - invoke stop of transformation
                               :  '-move x y z'                     - move attached object
                               :  '-rotate x y z dx dy dz angle'    - rotate attached object
                               :  '-scale factor'                   - scale attached object
                               :  '-autoActivate      {0|1}'        - set activation on detection
                               :  '-followTranslation {0|1}'        - set following translation transform
                               :  '-followRotation    {0|1}'        - set following rotation transform
                               :  '-followDragging    {0|1}'        - set following dragging transform
                               :  '-gap value'                      - set gap between sub-parts
                               :  '-part axis mode    {0|1}'        - set visual part
                               :  '-parts axis mode   {0|1}'        - set visual part
                               :  '-pos x y z [nx ny nz [xx xy xz]' - set position of manipulator
                               :  '-size value'                     - set size of manipulator
                               :  '-zoomable {0|1}'                 - set zoom persistence
vmarkerstest                   : vmarkerstest: name X Y Z [PointsOnSide=10] [MarkerType=0] [Scale=1.0] [FileName=ImageFile]
vmemgpu                        : vmemgpu [f]: print system-dependent GPU memory information if available;
                               : with f option returns free memory in bytes.
vmovedim                       : vmovedim [name] [x y z]
                               : Moves picked or named (if name defined)
                               : dimension to picked mouse position or input point.
                               : Text label of dimension 'name' is moved to position, another parts of dimension are adjusted.
vmoveto                        : vmoveto [x y] [-reset]
                               : Emulate cursor movement to pixel position (x,y).
                               :  -reset resets current highlighting.
vmoveview                      : vmoveview Dx Dy Dz [Start = 1|0]
vnbdisplayed                   : vnbdisplayed : Returns number of displayed objects
vnbselected                    : vnbselected : Returns number of selected objects in the interactive context.
vnormals                       : vnormals Shape [{on|off}=on] [-length {10}] [-nbAlongU {1}] [-nbAlongV {1}] [-nbAlong {1}]
                               :                [-useMesh] [-oriented {0}1}=0]
                               : Displays/Hides normals calculated on shape geometry or retrieved from triangulation
vobjzlayer                     : vobjzlayer : set/get object [layerid] - set or get z layer id for the interactive object
vpan                           : vpan dx dy
vparent                        : vparent parent [-ignoreVisu]
                               : Command for testing object properties as parent in the hierarchy.
                               :  -ignoreVisu do not propagate the visual state (display/erase/color) to children objects
vpbrenv                        : vpbrenv -clear|-generate
                               : Clears or generates PBR environment map of active view.
                               :  -clear clears PBR environment (fills by white color);
                               :  -generate generates PBR environment from current background cubemap.
vpick                          : vpick X Y Z [shape subshape]
vpickselected                  : vpickselected [name]: extract selected shape.
vpickshapes                    : vpickshape subtype(VERTEX,EDGE,WIRE,FACE,SHELL,SOLID) [name1 or .] [name2 or .] [name n or .]
                               : Hold Ctrl and pick object by clicking Left mouse button.
                               : Hold also Shift for multiple selection.
vplace                         : vplace dx dy : Places the point (in pixels) at the center of the window
vplane                         : vplane PlaneName [AxisName/PlaneName/PointName]
                               :        [PointName/PointName/PointName] [Nothing/Nothing/PointName] [TypeOfSensitivity {0|1}]
                               : Creates a plane from named or interactively selected entities. TypeOfSensitivity:
                               :   0 - Interior;
                               :   1 - Boundary.
vplaneortho                    : vplaneortho  PlaneName
                               : Creates a plane from interactive selected face and coplanar edge.
vplanepara                     : vplanepara  PlaneName
                               : Creates a plane from interactively selected vertex and face.
vplanetri                      : vplanetri name
                               : Create a plane from a trihedron selection.
                               : If no arguments are set, the default plane is created.
vpoint                         : vpoint name [X Y [Z]] [-2d] [-nosel]
                               : Creates a point from coordinates.
                               : If the values are not defined, a point is created from selected vertex or edge (center).
                               :  -2d    defines on-screen 2D point from top-left window corner;
                               :  -nosel creates non-selectable presentation.
vpointcloud                    : vpointcloud name shape [-randColor] [-normals] [-noNormals] [-uv]
                               : Create an interactive object for arbitrary set of points from triangulated shape.
                               : 
                               : vpointcloud name x y z r npts {surface|volume}
                               :             ... [-randColor] [-normals] [-noNormals] [-uv]
                               : Create arbitrary set of points (npts) randomly distributed
                               : on spheric surface or within spheric volume (x y z r).
                               : 
                               : Additional options:
                               :  -randColor - generate random color per point
                               :  -normals   - generate normal per point (default)
                               :  -noNormals - do not generate normal per point
vpolygonoffset                 : vpolygonoffset [object [mode factor units]]
                               : Sets/gets polygon offset parameters for an object; without arguments prints the default values
vpriority                      : vpriority [-noupdate|-update] name [value]
                               : Prints or sets the display priority for an object.
vpriviledgedplane              : vpriviledgedplane [Ox Oy Oz Nx Ny Nz [Xx Xy Xz]]
                               : Sets or prints viewer's priviledged plane geometry:
                               :   Ox, Oy, Oz - plane origin;
                               :   Nx, Ny, Nz - plane normal direction;
                               :   Xx, Xy, Xz - plane x-reference axis direction.
vraytrace                      : vraytrace [0|1] : Turns on/off ray-tracing renderer.
                               :  'vraytrace 0' alias for 'vrenderparams -raster'.
                               :  'vraytrace 1' alias for 'vrenderparams -rayTrace'.
vreadpixel                     : vreadpixel xPixel yPixel [{rgb|rgba|sRGB|sRGBa|depth|hls|rgbf|rgbaf}=rgba] [-name|-hex]
                               : Read pixel value for active view.
vrelation                      : vrelation name {-concentric|-equaldistance|-equalradius|-fix|
                               :                 -identic|-offset|-parallel|-perpendicular|-tangent|-symmetric}
                               : Builds specific relation from selected objects:
                               :  -concentric    - 2 circled edges
                               :  -equaldistance - 4 vertex/edges
                               :  -equalradius   - 1 or 2 circled edges
                               :  -fix           - 1 edge
                               :  -identic       - 2 faces, edges or vertices
                               :  -offset        - 2 faces
                               :  -parallel      - 2 faces or 2 edges
                               :  -perpendicular - 2 faces or 2 edges
                               :  -tangent       - two coplanar edges (first the circular edge then the tangent edge) or two faces
                               :  -symmetric     - 3 edges or 1 edge and 2 vertices
vremove                        : vremove [-noupdate|-update] [-context] [-all] [-noinfo] [name1] ...  [name n] [-noerror]
                               : or vremove [-context] -all to remove all objects
                               : Removes selected or named objects.
                               :  -context  do not delete object from the map of objects and names;
                               :  -noupdate suppresses viewer redraw call;
                               :  -noinfo   suppresses displaying the list of removed objects;
                               :  -noerror  prevents exception on non-existing objects.
vrenderparams                  : Manages rendering parameters, affecting visual appearance, quality and performance.
                               : Should be applied taking into account GPU hardware capabilities and performance.
                               : 
                               : Common parameters:
                               : vrenderparams [-raster] [-shadingModel {unlit|facet|gouraud|phong|pbr|pbr_facet}=gouraud]
                               :               [-msaa 0..8=0] [-rendScale scale=1]
                               :               [-resolution value=72] [-fontHinting {off|normal|light}=off]
                               :               [-fontAutoHinting {auto|force|disallow}=auto]
                               :               [-oit {off|weight|peel}] [-oit weighted [depthFactor=0.0]] [-oit peeling [nbLayers=4]]
                               :               [-shadows {on|off}=on] [-shadowMapResolution value=1024] [-shadowMapBias value=0.005]
                               :               [-depthPrePass {on|off}=off] [-alphaToCoverage {on|off}=on]
                               :               [-frustumCulling {on|off|noupdate}=on] [-lineFeather width=1.0]
                               :               [-sync {default|views}] [-reset]
                               :  -raster          Disables GPU ray-tracing.
                               :  -shadingModel    Controls shading model.
                               :  -msaa            Specifies number of samples for MSAA.
                               :  -rendScale       Rendering resolution scale factor (supersampling, alternative to MSAA).
                               :  -resolution      Sets new pixels density (PPI) used as text scaling factor.
                               :  -fontHinting     Enables/disables font hinting for better readability on low-resolution screens.
                               :  -fontAutoHinting Manages font autohinting.
                               :  -lineFeather     Sets line feather factor while displaying mesh edges.
                               :  -alphaToCoverage Enables/disables alpha to coverage (needs MSAA).
                               :  -oit             Enables/disables order-independent transparency (OIT) rendering;
                               :       off         unordered transparency (but opaque objects implicitly draw first);
                               :       weighted    weight OIT is managed by depth weight factor 0.0..1.0;
                               :       peeling     depth peeling OIT is managed by number of peeling layers.
                               :   -shadows         Enables/disables shadows rendering.
                               :   -shadowMapResolution Shadow texture map resolution.
                               :   -shadowMapBias   Shadow map bias.
                               :   -depthPrePass    Enables/disables depth pre-pass.
                               :   -frustumCulling  Enables/disables objects frustum clipping or
                               :                    sets state to check structures culled previously.
                               :   -sync            Sets active View parameters as Viewer defaults / to other Views.
                               :   -reset           Resets active View parameters to Viewer defaults.
                               : 
                               : Diagnostic output (on-screen overlay):
                               : vrenderparams [-perfCounters none|fps|cpu|layers|structures|groups|arrays|triangles|points
                               :                                  |gpuMem|frameTime|basic|extended|full|nofps|skipImmediate]
                               :               [-perfUpdateInterval nbSeconds=1] [-perfChart nbFrames=1] [-perfChartMax seconds=0.1]
                               :  -perfCounters       Show/hide performance counters (flags can be combined).
                               :  -perfUpdateInterval Performance counters update interval.
                               :  -perfChart          Show frame timers chart limited by specified number of frames.
                               :  -perfChartMax       Maximum time in seconds with the chart.
                               : 
                               : Ray-Tracing options:
                               : vrenderparams [-rayTrace] [-rayDepth {0..10}=3] [-reflections {on|off}=off]
                               :               [-fsaa {on|off}=off] [-gleam {on|off}=off] [-env {on|off}=off]
                               :               [-gi {on|off}=off] [-brng {on|off}=off]
                               :               [-iss {on|off}=off] [-tileSize {1..4096}=32] [-nbTiles {64..1024}=256]
                               :               [-ignoreNormalMap {on|off}=off] [-twoSide {on|off}=off]
                               :               [-maxRad {value>0}=30.0]
                               :               [-aperture {value>=0}=0.0] [-focal {value>=0.0}=1.0]
                               :               [-exposure value=0.0] [-whitePoint value=1.0] [-toneMapping {disabled|filmic}=disabled]
                               :  -rayTrace     Enables  GPU ray-tracing.
                               :  -rayDepth     Defines maximum ray-tracing depth.
                               :  -reflections  Enables/disables specular reflections.
                               :  -fsaa         Enables/disables adaptive anti-aliasing.
                               :  -gleam        Enables/disables transparency shadow effects.
                               :  -gi           Enables/disables global illumination effects (Path-Tracing).
                               :  -env          Enables/disables environment map background.
                               :  -ignoreNormalMap Enables/disables normal map ignoring during path tracing.
                               :  -twoSide      Enables/disables two-sided BSDF models (PT mode).
                               :  -iss          Enables/disables adaptive screen sampling (PT mode).
                               :  -maxRad       Value used for clamping radiance estimation (PT mode).
                               :  -tileSize     Specifies   size of screen tiles in ISS mode (32 by default).
                               :  -nbTiles      Specifies number of screen tiles per Redraw in ISS mode (256 by default).
                               :  -aperture     Aperture size  of perspective camera for depth-of-field effect (0 disables DOF).
                               :  -focal        Focal distance of perspective camera for depth-of-field effect.
                               :  -exposure     Exposure value for tone mapping (0.0 value disables the effect).
                               :  -whitePoint   White point value for filmic tone mapping.
                               :  -toneMapping  Tone mapping mode (disabled, filmic).
                               : 
                               : PBR environment baking parameters (advanced/debug):
                               : vrenderparams [-pbrEnvPow2size {power>0}=9] [-pbrEnvSMLN {levels>1}=6] [-pbrEnvBP {0..1}=0.99]
                               :               [-pbrEnvBDSN {samples>0}=1024] [-pbrEnvBSSN {samples>0}=256]
                               :  -pbrEnvPow2size Controls size of IBL maps (real size can be calculates as 2^pbrenvpow2size).
                               :  -pbrEnvSMLN     Controls number of mipmap levels used in specular IBL map.
                               :  -pbrEnvBDSN     Controls number of samples in Monte-Carlo integration during
                               :                  diffuse IBL map's sherical harmonics calculation.
                               :  -pbrEnvBSSN     Controls maximum number of samples per mipmap level
                               :                  in Monte-Carlo integration during specular IBL maps generation.
                               :  -pbrEnvBP       Controls strength of samples number reducing
                               :                  during specular IBL maps generation (1 disables reducing).
                               : 
                               : Debug options:
                               : vrenderparams [-issd {on|off}=off] [-rebuildGlsl on|off]
                               :  -issd         Shows screen sampling distribution in ISS mode.
                               :  -rebuildGlsl  Rebuild Ray-Tracing GLSL programs (for debugging).
                               :  -brng         Enables/disables blocked RNG (fast coherent PT).
vrepaint                       : vrepaint [-immediate] [-continuous FPS]
                               : Force redraw of active View.
                               :  -immediate  flag performs redraw of immediate layers only;
                               :  -continuous activates/deactivates continuous redraw of active View,
                               :              0 means no continuous rendering,
                               :             -1 means non-stop redraws,
                               :             >0 specifies target framerate.
vright                         : vright : Display right view (+Y+Z) in the 3D viewer window.
vrotate                        : vrotate [[-mouseStart X Y] [-mouseMove X Y]]|[AX AY AZ [X Y Z]]
                               :  -mouseStart start rotation according to the mouse position;
                               :  -mouseMove  continue rotation with angle computed
                               :              from last and new mouse position.
vscale                         : vscale X Y Z
vsegment                       : vsegment Name PointName PointName
                               : Creates and displays a segment from named points.
vselaxis                       : vselaxis x y z dx dy dz [-onlyTop 0|1] [-display Name] [-showNormal 0|1]"
                               : Provides intersection by given axis and print result intersection points.
                               :  -onlyTop       switches On/Off mode to find only top point or all;
                               :  -display Name  displays intersecting axis and result intersection points for debug goals;
                               :  -showNormal    adds displaying of normal in intersection point or not.
vselbvhbuild                   : vselbvhbuild [{0|1}] [-nbThreads value] [-wait]
                               : Turns on/off prebuilding of BVH within background thread(s).
                               :  -nbThreads   number of threads, 1 by default; if < 1 then used (NbLogicalProcessors - 1);
                               :  -wait        waits for building all of BVH.
vseldump                       : vseldump file -type {depth|unnormDepth|object|owner|selMode|entity|entityType|surfNormal}=depth
                               :          -pickedIndex Index=1
                               :          [-xrPose base|head=base]
                               : Generate an image based on detection results:
                               :   depth       normalized depth values
                               :   unnormDepth unnormalized depth values
                               :   object      color of detected object
                               :   owner       color of detected owner
                               :   selMode     color of selection mode
                               :   entity      color of detected entity
                               :   entityType  color of detected entity type
                               :   surfNormal  normal direction values
vselect                        : vselect x1 y1 [x2 y2 [x3 y3 ... xn yn]] [-allowoverlap 0|1]
                               :         [-replace|-replaceextra|-xor|-add|-remove]
                               : Emulate different types of selection:
                               :  1) Single click selection.
                               :  2) Selection with rectangle having corners at pixel positions (x1,y1) and (x2,y2).
                               :  3) Selection with polygon having corners in pixel positions (x1,y1), (x2,y2),...,(xn,yn).
                               :  4) -allowoverlap manages overlap and inclusion detection in rectangular and polygonal selection.
                               :     If the flag is set to 1, both sensitives that were included completely
                               :     and overlapped partially by defined rectangle or polygon will be detected,
                               :     otherwise algorithm will chose only fully included sensitives.
                               :     Default behavior is to detect only full inclusion
                               :     (partial inclusion - overlap - is not allowed by default).
                               :  5) Selection scheme replace, replaceextra, xor, add or remove (replace by default).
vselfilter                     : vselfilter [-contextfilter {AND|OR}]
                               :            [-type {VERTEX|EDGE|WIRE|FACE|SHAPE|SHELL|SOLID}]
                               :            [-secondtype {VERTEX|EDGE|WIRE|FACE|SHAPE|SHELL|SOLID}]
                               :            [-clear]
                               : Sets selection shape type filter in context or remove all filters.
                               :  -contextfilter to define a selection filter for two or more types of entity,
                               :                 use value AND (OR by default).
                               :  -type  set type of selection filter; filters are applied with Or combination.
                               :  -clear remove all filters in context.
vselmode                       : vselmode [object] selectionMode {on|off}
                               :          [{-add|-set|-globalOrLocal}=-globalOrLocal]
                               : Switches selection mode for the specified object or for all objects in context.
                               : Selection mode is either an integer number specific to Interactive Object,
                               : or sub-shape type in case of AIS_Shape:
                               :   Shape, Vertex, Edge, Wire, Face, Shell, Solid, CompSolid, Compound
                               : The integer mode 0 (Shape in case of AIS_Shape) is reserved for selecting object as whole.
                               : Additional options:
                               :  -add           already activated selection modes will be left activated
                               :  -set           already activated selection modes will be deactivated
                               :  -globalOrLocal (default) if new mode is Global selection mode,
                               :                 then active local selection modes will be deactivated
                               :                 and the samthen active local selection modes will be deactivated
vselnext                       : vselnext : hilight next detected
vselprev                       : vselnext : hilight previous detected
vselprops                      : vselprops [dynHighlight|localDynHighlight|selHighlight|localSelHighlight] [options]
                               : Customizes selection and dynamic highlight parameters for the whole interactive context:
                               :  -autoActivate {0|1}     disables|enables default computation
                               :                          and activation of global selection mode
                               :  -autoHighlight {0|1}    disables|enables automatic highlighting in 3D Viewer
                               :  -highlightSelected {0|1} disables|enables highlighting of detected object in selected state
                               :  -pickStrategy {first|topmost} : defines picking strategy
                               :                'first'   to pick first acceptable (default)
                               :                'topmost' to pick only topmost (and nothing, if topmost is rejected by filters)
                               :  -pixTol    value        sets up pixel tolerance
                               :  -depthTol {uniform|uniformpx} value : sets tolerance for sorting results by depth
                               :  -depthTol {sensfactor}  use sensitive factor for sorting results by depth
                               :  -preferClosest {0|1}    sets if depth should take precedence over priority while sorting results
                               :  -dispMode  dispMode     sets display mode for highlighting
                               :  -layer     ZLayer       sets ZLayer for highlighting
                               :  -color     {name|r g b} sets highlight color
                               :  -transp    value        sets transparency coefficient for highlight
                               :  -material  material     sets highlight material
                               :  -print                  prints current state of all mentioned parameters
vsensdis                       : vsensdis : Display active entities
                               : (sensitive entities of one of the standard types corresponding to active selection modes).
                               : Standard entity types are those defined in Select3D package:
                               :  - sensitive box, face, curve, segment, circle, point, triangulation, triangle.
                               : Custom (application-defined) sensitive entity types are not processed by this command.
vsensera                       : vsensera : erase active entities
vsetbg                         : Alias for 'vbackground -imageFile ImageFile [-imageMode FillType]'.
vsetbgmode                     : Alias for 'vbackground -imageMode FillType'.
vsetcolor                      : vsetcolor [-noupdate|-update] [name] ColorName
                               : Sets color for all, selected or named objects.
                               : Alias for vaspects -setcolor [name] ColorName.
vsetcolorbg                    : Alias for 'vbackground -color Color'.
vsetdefaultbg                  : Alias for 'vbackground -default -gradient Color1 Color2 [-gradientMode FillMethod]'
                               :   and for 'vbackground -default -color Color'.
vsetdispmode                   : vsetdispmode [name] mode(1,2,..)
                               : Sets display mode for all, selected or named objects.
                               : In case of a shape presentation, 0 defines WireFrame, and 1 defines Shading display modes.
vsetedgetype                   : vsetedgetype [name] [-type {solid, dash, dot}] [-color R G B] [-width value]
                               : Alias for vaspects [name] -setEdgeType Type.
vsetgradientbg                 : Alias for 'vbackground -gradient Color1 Color2 -gradientMode FillMethod'.
vsetgrbgmode                   : Alias for 'vbackground -gradientMode FillMethod'.
vsetinteriorstyle              : vsetinteriorstyle [-noupdate|-update] [name] Style
                               : Alias for vaspects -setInterior [name] Style.
vsetlocation                   : Alias for vlocation
vsetmaterial                   : vsetmaterial [-noupdate|-update] [name] MaterialName
                               : n\t\t: Alias for vaspects -setmaterial [name] MaterialName.
vsetshading                    : vsetshading name Quality(default=0.0008)
                               : Sets deflection coefficient that defines the quality of the shape representation in the shading mode.
vsettransparency               : vsettransparency [-noupdate|-update] [name] Coefficient
                               : Sets transparency for all, selected or named objects.
                               : The Coefficient may be between 0.0 (opaque) and 1.0 (fully transparent).
                               : Alias for vaspects -settransp [name] Coefficient.
vsetviewsize                   : vsetviewsize size
vsetwidth                      : vsetwidth [-noupdate|-update] [name] width(0->10)
                               : Alias for vaspects -setwidth [name] width.
vshader                        : vshader name -vert VertexShader -frag FragmentShader [-geom GeometryShader]
                               :         [-off] [-phong] [-aspect {shading|line|point|text}=shading]
                               :         [-header VersionHeader]
                               :         [-tessControl TessControlShader -tessEval TessEvaluationShader]
                               :         [-uniform Name FloatValue]
                               : Assign custom GLSL program to presentation aspects.
vshaderprog                    : Alias for vshader
vshowfaceboundary              : vshowfaceboundary [name]: Alias for vaspects [name] -setFaceBoundaryDraw on.
vsize                          : vsize [name(Default=Current)] [size(Default=100)]
                               : Changes the size of a named or selected trihedron.
                               : If the name is not defined: it affects the selected trihedrons otherwise nothing is done.
                               : If the value is not defined: it is set to 100 by default.
vsphere                        : vsphere name [-radius] R
                               :              [-nbSlices Number=100] [-nbStacks Number=100] [-noupdate]
                               : Creates and displays a sphere.
vstate                         : vstate [-entities] [-hasSelected] [name1] ... [nameN]
                               : Reports show/hidden state for selected or named objects.
                               :  -entities    prints low-level information about detected entities;
                               :  -hasSelected prints 1 if context has selected shape and 0 otherwise.
vstatprofiler                  : vstatprofiler [fps|cpu|allLayers|layers|allstructures|structures|groups
                               :                 |allArrays|fillArrays|lineArrays|pointArrays|textArrays
                               :                 |triangles|points|geomMem|textureMem|frameMem
                               :                 |elapsedFrame|cpuFrameAverage|cpuPickingAverage|cpuCullingAverage|cpuDynAverage
                               :                 |cpuFrameMax|cpuPickingMax|cpuCullingMax|cpuDynMax]
                               :               [-noredraw]
                               : Prints rendering statistics for specified counters or for all when unspecified.
                               : Set '-noredraw' flag to avoid additional redraw call and use already collected values.
vstereo                        : vstereo [0|1] [-mode Mode] [-reverse {0|1}]
                               :         [-mirrorComposer] [-hmdfov2d AngleDegrees] [-unitFactor MetersFactor]
                               :         [-anaglyph Filter]
                               : Control stereo output mode. Available modes for -mode:
                               :   quadBuffer       OpenGL QuadBuffer stereo;
                               :     requires driver support;
                               :     should be called BEFORE vinit!
                               :   anaglyph         Anaglyph glasses, filters for -anaglyph:
                               :     redCyan, redCyanSimple, yellowBlue, yellowBlueSimple, greenMagentaSimple.
                               :   rowInterlaced    row-interlaced display
                               :   columnInterlaced column-interlaced display
                               :   chessBoard       chess-board output
                               :   sideBySide       horizontal pair
                               :   overUnder        vertical   pair
                               :   openVR           OpenVR (HMD), extra options:
                               :     -mirrorComposer flag to mirror VR frame in the window (debug);
                               :     -unitFactor     specifies meters scale factor for mapping VR input.
vsub                           : vsub 0/1 (off/on) [obj] : Subintensity(on/off) of selected objects
vtexdefault                    : vtexdefault name : Alias for vtexture name -default.
vtexorigin                     : vtexorigin name OriginU OriginV
                               : Alias for vtexture name -setOrigin OriginU OriginV.
vtexrepeat                     : vtexrepeat name RepeatU RepeatV
                               : Alias for vtexture name -setRepeat RepeatU RepeatV.
vtexscale                      : vtexscale name ScaleU ScaleV
                               : Alias for vtexture name -setScale ScaleU ScaleV.
vtexture                       : vtexture [-noupdate|-update] name [ImageFile|IdOfTexture|off]
                               :          [-tex0 Image0] [-tex1 Image1] [...]
                               :          [-origin {u v|off}] [-scale {u v|off}] [-repeat {u v|off}]
                               :          [-trsfTrans du dv] [-trsfScale su sv] [-trsfAngle Angle]
                               :          [-modulate {on|off}] [-srgb {on|off}]=on
                               :          [-setFilter {nearest|bilinear|trilinear}]
                               :          [-setAnisoFilter {off|low|middle|quality}]
                               :          [-default]
                               : The texture can be specified by filepath
                               : or as ID (0<=IdOfTexture<=20) specifying one of the predefined textures.
                               : The options are:
                               :  -scale     Setup texture scaling for generating coordinates; (1, 1) by default
                               :  -origin    Setup texture origin  for generating coordinates; (0, 0) by default
                               :  -repeat    Setup texture repeat  for generating coordinates; (1, 1) by default
                               :  -modulate  Enable or disable texture color modulation
                               :  -srgb      Prefer sRGB texture format when applicable; TRUE by default
                               :  -trsfAngle Setup dynamic texture coordinates transformation - rotation angle
                               :  -trsfTrans Setup dynamic texture coordinates transformation - translation vector
                               :  -trsfScale Setup dynamic texture coordinates transformation - scale vector
                               :  -setFilter Setup texture filter
                               :  -setAnisoFilter Setup anisotropic filter for texture with mip-levels
                               :  -default   Sets texture mapping default parameters
vtextureenv                    : vtextureenv {on|off} {image_file}
                               :             [{clamp|repeat} {decal|modulate} {nearest|bilinear|trilinear} ss st ts tt rot]
                               : Enables or disables environment mapping in the 3D view, loading the texture from the given standard
                               : or user-defined file and optionally applying texture mapping parameters.
                               :  ss, st - scale factors for s and t texture coordinates;
                               :  ts, tt - translation for s and t texture coordinates;
                               :  rot    - texture rotation angle in degrees.
vtile                          : vtile [-totalSize W H] [-lowerLeft X Y] [-upperLeft X Y] [-tileSize W H]
                               : Setup view to draw a tile (a part of virtual bigger viewport).
                               :  -totalSize the size of virtual bigger viewport
                               :  -tileSize  tile size (the view size will be used if omitted)
                               :  -lowerLeft tile offset as lower left corner
                               :  -upperLeft tile offset as upper left corner
vtop                           : vtop or <T> : Display top view (+X+Y) in the 3D viewer window.
vtorus                         : vtorus name [R1 R2 [Angle1=0 Angle2=360] [Angle=360]]
                               :        [-radius R1] [-pipeRadius R2]
                               :        [-pipeAngle Angle=360] [-segmentAngle1 Angle1=0 -segmentAngle2 Angle2=360]
                               :        [-nbSlices Number=100] [-nbStacks Number=100] [-noupdate]
                               : Creates and displays a torus or torus segment.
                               : Parameters of the torus:
                               :  - R1     distance from the center of the pipe to the center of the torus
                               :  - R2     radius of the pipe
                               :  - Angle1 first angle to create a torus ring segment
                               :  - Angle2 second angle to create a torus ring segment
                               :  - Angle  angle to create a torus pipe segment
vtranslateview                 : vtranslateview Dx Dy Dz [Start = 1|0)]
vtri2d                         : vtri2d Name : Creates a plane with a 2D trihedron from an interactively selected face.
vtriangle                      : vtriangle Name PointName PointName PointName
                               : Creates and displays a filled triangle from named points.
vtrihedron                     : vtrihedron name
                               :            [-dispMode {wireframe|shading} ]
                               :            [-origin x y z ]
                               :            [-zaxis u v w -xaxis u v w ]
                               :            [-drawAxes {X|Y|Z|XY|YZ|XZ|XYZ}]
                               :            [-hideLabels {on|off}]
                               :            [-hideArrows {on|off}]
                               :            [-label {XAxis|YAxis|ZAxis} value]
                               :            [-attribute {XAxisLength|YAxisLength|ZAxisLength
                               :                        |TubeRadiusPercent|ConeRadiusPercent
                               :                        |ConeLengthPercent|OriginRadiusPercent
                               :                        |ShadingNumberOfFacettes} value]
                               :            [-color {Origin|XAxis|YAxis|ZAxis|XOYAxis|YOZAxis
                               :                    |XOZAxis|Whole} {r g b | colorName}]
                               :            [-textColor  [XAxis|YAxis|ZAxis] {r g b | colorName}]
                               :            [-arrowColor [XAxis|YAxis|ZAxis] {r g b | colorName}]
                               :            [-priority {Origin|XAxis|YAxis|ZAxis|XArrow
                               :                       |YArrow|ZArrow|XOYAxis|YOZAxis
                               :                       |XOZAxis|Whole} value]
                               : 
                               : Creates/changes *AIS_Trihedron* object.
                               :  -dispMode   mode of visualization: wf - wireframe,
                               :                                     sh - shading;
                               :              default value is wireframe;
                               :  -origin     allows to set trihedron location;
                               :  -zaxis/-xaxis allows to set trihedron X and Z directions;
                               :              the directions should be orthogonal;
                               :              Y direction is calculated;
                               :  -drawAxes   allows to set what axes are drawn in the
                               :              trihedron, default state is XYZ;
                               :  -hideLabels allows to show/hide trihedron labels;
                               :  -hideArrows allows to show/hide trihedron arrows;
                               :  -label      allows to change default X/Y/Z titles of axes;
                               :  -attribute  sets parameters of trihedron;
                               :  -color      sets color properties of parts of trihedron;
                               :  -textColor  sets color properties of trihedron labels;
                               :  -arrowColor sets color properties of trihedron arrows;
                               :  -priority   allows to change default selection priority
                               :              of trihedron components.
vturnview                      : vturnview Ax Ay Az [Start = 1|0]
vtypes                         : vtypes : list of known types and signatures in AIS.
                               : To be Used in vpickobject command for selection with filters.
vunsetcolor                    : vunsetcolor [-noupdate|-update] [name]
                               : Resets color for all, selected or named objects.
                               : Alias for vaspects -unsetcolor [name].
vunsetdispmode                 : vunsetdispmode [name]
                               : Unsets custom display mode for selected or named objects.
vunsetedgetype                 : vunsetedgetype [name] : Alias for vaspects [name] -unsetEdgeType.
vunsetmaterial                 : vunsetmaterial [-noupdate|-update] [name]
                               : Alias for vaspects -unsetmaterial [name].
vunsetshading                  : vunsetshading name
                               : Sets default deflection coefficient (0.0008) that defines the quality of the shape representation in the shading mode.
vunsettransparency             : vunsettransparency [-noupdate|-update] [name]
                               : Resets transparency for all, selected or named objects.
                               : Alias for vaspects -unsettransp [name].
vunsetwidth                    : vunsetwidth [-noupdate|-update] [name]
                               : Alias for vaspects -unsetwidth [name].
vupdate                        : vupdate name1 [name2] ... [name n]
                               : Updates named objects in interactive context
vvertexmode                    : vvertexmode [name | -set {isolated|all|inherited} [name1 name2 ...]]
                               : Sets the vertex draw mode for the specified object(s)
                               : or sets default vertex draw mode and updates the mode for all displayed objects.
                               : Prints the default vertex draw mode without -set parameter.
vviewcube                      : vviewcube name
                               : Displays interactive view manipulation object. Options:
                               :  -reset                   reset geometric and visual attributes
                               :  -size Size               adapted size of View Cube
                               :  -boxSize Size            box size
                               :  -axes  {0|1}             show/hide axes (trihedron)
                               :  -edges {0|1}             show/hide edges of View Cube
                               :  -vertices {0|1}          show/hide vertices of View Cube
                               :  -Yup {0|1} -Zup {0|1}    set Y-up or Z-up view orientation
                               :  -color Color             color of View Cube
                               :  -boxColor Color          box color
                               :  -boxSideColor Color      box sides color
                               :  -boxEdgeColor Color      box edges color
                               :  -boxCornerColor Color    box corner color
                               :  -textColor Color         color of side text of view cube
                               :  -innerColor Color        inner box color
                               :  -transparency Value      transparency of object within [0, 1] range
                               :  -boxTransparency Value   transparency of box    within [0, 1] range
                               :  -xAxisTextColor Color    color of X axis label
                               :  -yAxisTextColor Color    color of Y axis label
                               :  -zAxisTextColor Color    color of Z axis label
                               :  -font Name               font name
                               :  -fontHeight Value        font height
                               :  -boxFacetExtension Value box facet extension
                               :  -boxEdgeGap Value        gap between box edges and box sides
                               :  -boxEdgeMinSize Value    minimal box edge size
                               :  -boxCornerMinSize Value  minimal box corner size
                               :  -axesPadding Value       padding between box and arrows
                               :  -roundRadius Value       relative radius of corners of sides within [0.0, 0.5] range
                               :  -axesRadius Value        radius of axes of the trihedron
                               :  -axesConeRadius Value    radius of the cone (arrow) of the trihedron
                               :  -axesSphereRadius Value  radius of the sphere (central point) of trihedron
                               :  -fixedAnimation {0|1}    uninterruptible animation loop
                               :  -duration Seconds        animation duration in seconds
vviewlist                      : vviewlist [format={tree, long}]=tree
                               : Prints current list of views per viewer and graphic_driver ID shared between viewers
                               :  - format: format of result output, if tree the output is a tree view;
                               :            otherwise it's a list of full view names.
vviewparams                    : vviewparams [-args] [-scale [s]]
                               :             [-eye [x y z]] [-at [x y z]] [-up [x y z]]
                               :             [-proj [x y z]] [-center x y] [-size sx]
                               : Manage current view parameters (camera orientation) or prints all
                               : current values when called without argument.
                               :  -scale [s]    prints or sets viewport relative scale
                               :  -eye  [x y z] prints or sets eye location
                               :  -at   [x y z] prints or sets center of look
                               :  -up   [x y z] prints or sets direction of up vector
                               :  -proj [x y z] prints or sets direction of look
                               :  -center x y   sets location of center of the screen in pixels
                               :  -size [sx]    prints viewport projection width and height sizes
                               :                or changes the size of its maximum dimension
                               :  -args         prints vviewparams arguments for restoring current view
vviewproj                      : vviewproj [top|bottom|left|right|front|back|axoLeft|axoRight]
                               :           [+-X+-Y+-Z] [-Zup|-Yup] [-frame +-X+-Y]
                               : Setup view direction
                               :  -Yup      use Y-up convention instead of Zup (which is default).
                               :  +-X+-Y+-Z define direction as combination of DX, DY and DZ;
                               :            for example '+Z' will show front of the model,
                               :            '-X-Y+Z' will define left axonometric view.
                               :  -frame    define camera Up and Right directions (regardless Up convention);
                               :            for example '+X+Z' will show front of the model with Z-up.
vxrotate                       : vxrotate
vzbufftrihedron                : vzbufftrihedron [{-on|-off}=-on] [-type {wireframe|zbuffer}=zbuffer]
                               :        [-position center|left_lower|left_upper|right_lower|right_upper]
                               :        [-scale value=0.1] [-size value=0.8] [-arrowDiam value=0.05]
                               :        [-colorArrowX color=RED] [-colorArrowY color=GREEN] [-colorArrowZ color=BLUE]
                               :        [-nbfacets value=12] [-colorLabels color=WHITE]
                               :        [-colorLabelX color] [-colorLabelY color] [-colorLabelZ color]
                               : Displays a trihedron.
vzfit                          : vzfit [scale]
                               : Automatic depth panning.
                               : Matches Z near, Z far view volume planes to the displayed objects.
                               :  - "scale" specifies factor to scale computed z range.
vzlayer                        : vzlayer [layerId]
                               :         [-add|-delete|-get|-settings] [-insertBefore AnotherLayer] [-insertAfter AnotherLayer]
                               :         [-origin X Y Z] [-cullDist Distance] [-cullSize Size]
                               :         [-enable|-disable {depthTest|depthWrite|depthClear|depthoffset}]
                               :         [-enable|-disable {positiveOffset|negativeOffset|textureenv|rayTracing}]
                               : ZLayer list management
                               :  -add      add new z layer to viewer and print its id
                               :  -insertBefore add new z layer and insert it before existing one
                               :  -insertAfter  add new z layer and insert it after  existing one
                               :  -delete   delete z layer
                               :  -get      print sequence of z layers
                               :  -settings print status of z layer settings
                               :  -disable  disables given setting
                               :  -enable   enables  given setting
vzoom                          : vzoom coef
vzrange                        : vzrange [znear] [zfar]
                               : Applies provided znear/zfar to view or prints current values.
attachpcurve                   : attachpcurve eold enew face
b2dclassifx                    : use b2dclassifx Face Point2d [Tol] 
b2dclassify                    : use b2dclassify Face Point2d [Tol] [UseBox] [GapCheckTol]
                               : Classify  the Point  Point2d  with  Tolerance <Tol> on the face described by <Face>.
                               : <UseBox> == 1/0 (default <UseBox> = 0): switch on/off the use Bnd_Box in the classification.
                               : <GapCheckTol> (default <GapCheckTol> = 0.1): this is for additional verification of
                               : the vertex with a tolerance >= <GapCheckTol>.
baddcompound                   : Command for adding multiple objects for Boolean/GF/Split/Cells operations grouped in one object.
                               :         Given object will be exploded on first level sub-shapes and each of these sub-shapes will act as a separate object.
                               :         The command has cumulative effect, thus can be used several times for single operation.
                               :         For new operation the objects have to be cleared by bclearobjects or bclear commands.
                               :         Usage: baddcompound c
baddctools                     : Command for adding multiple tools for Boolean/GF/Split/Cells operations grouped in one object.
                               :         Given object will be exploded on first level sub-shapes and each of these sub-shapes will act as a separate tool.
                               :         The command has cumulative effect, thus can be used several times for single operation.
                               :         For new operation the tools have to be cleared by bcleartools or bclear commands.
                               :         Usage: baddctools c
baddobjects                    : Adds objects for Boolean/GF/Split/Cells operations.
                               :         The command has cumulative effect, thus can be used several times for single operation.
                               :         For new operation the objects have to be cleared by bclearobjects or bclear commands.
                               :         Usage: baddobjects s1 s2 ...
baddtools                      : Adds tools for Boolean/GF/Split/Cells operations.
                               :         The command has cumulative effect, thus can be used several times for single operation.
                               :         For new operation the tools have to be cleared by bcleartools or bclear commands.
                               :         Usage: baddtools s1 s2 ...
bapibop                        : Builds the result of Boolean operation using top level API.
                               :         Objects for the operation are added using commands baddobjects and baddtools.
                               :         Usage: bapibop r operation
                               :         Where:
                               :         result - name of the result shape
                               :         op - type of Boolean operation. Possible values:
                               :              - 0/common - for Common operation
                               :              - 1/fuse - for Fuse operation
                               :              - 2/cut - for Cut operation
                               :              - 3/tuc/cut21 - for Cut21 operation
                               :              - 4/section - for Section operation
bapibuild                      : Builds the result of General Fuse operation using top level API.
                               :         Objects for the operation are added using commands baddobjects and baddtools.
                               :         Usage: bapibuild result
bapisplit                      : Builds the result of Split operation using top level API.
                               :         Objects for the operation are added using commands baddobjects and baddtools.
                               :         Usage: bapisplit result
bbop                           : Builds the result of Boolean operation. Intersection (bfillds) has to be already performed by this moment.
                               :         Usage: bbop result op [-t]
                               :         Where:
                               :         result - name of the result shape
                               :         op - type of Boolean operation. Possible values:
                               :              - 0/common - for Common operation
                               :              - 1/fuse - for Fuse operation
                               :              - 2/cut - for Cut operation
                               :              - 3/tuc/cut21 - for Cut21 operation
                               :              - 4/section - for Section operation
                               :         -t - optional parameter for enabling timer and showing elapsed time of the operation
bbuild                         : Builds the result of General Fuse operation. Intersection (bfillds) has to be already performed by this moment.
                               :         Usage: bbuild result [-t]
                               :         Where:
                               :         result - name of the result shape
                               :         -t is the optional parameter for enabling timer and showing elapsed time of the operation
bcadd                          : Add parts to result. Use: bcadd r s1 (0,1) s2 (0,1) ... [-m material [-u]]
bcaddall                       : Add all parts to result. Use: bcaddall r [-m material [-u]]
bcbuild                        : Cells builder. Use: bcbuild r
bcheckinverted                 : Enables/Disables the check of the input solids on inverted status in BOP algorithms
                               :         Usage: bcheckinverted 0 (off) / 1 (on)
bclassify                      : use bclassify Solid Point [Tolerance=1.e-7]
bclear                         : Clears both objects and tools previously added for Boolean/GF/Split/Cells operations.
                               :         Usage: bclear
bclearobjects                  : Clears the objects previously added for Boolean/GF/Split/Cells operations.
                               :         Usage: bclearobjects
bcleartools                    : Clears the tools previously added for Boolean/GF/Split/Cells operations.
                               :         Usage: bcleartools
bcmakecontainers               : Make containers from the parts added to result. Use: bcmakecontainers r
bcommon                        : use bcommon r s1 s2
bcremove                       : Remove parts from result. Use: bcremove r s1 (0,1) s2 (0,1) ...
bcremoveall                    : Remove all parts from result. Use: bcremoveall
bcremoveint                    : Remove internal boundaries. Use: bcremoveint r
bcut                           : use bcut r s1 s2
bdrawwarnshapes                : Enables/Disables drawing of warning shapes of BOP algorithms.
                               :         Usage: bdrawwarnshapes 0 (do not draw) / 1 (draw warning shapes)
bfillds                        : Performs intersection of the arguments added for the operation by baddobjects and baddtools commands.
                               :         Usage: bfillds [-t]
                               :         Where: -t is the optional parameter for enabling timer and showing elapsed time of the operation
bfuse                          : use bfuse r s1 s2
bfuzzyvalue                    : Sets the additional tolerance for BOP algorithms.
                               :         Usage: bfuzzyvalue value
bglue                          : Sets the gluing mode for the BOP algorithms.
                               :         Usage: bglue [0 (off) / 1 (shift) / 2 (full)]
bhaspc                         : use bhaspc Edge Face [do]
bnondestructive                : Enables/Disables the safe processing mode.
                               :         Usage: bnondestructive 0/1
bop                            : use bop s1 s2
bopaddpcs                      : Use >bopaddpcs Shape
bopapicheck                    : Checks the validity of shape/pair of shapes.
                               :         Usage: bopapicheck s1 [s2] [-op common/fuse/cut/tuc] [-se] [-si]
                               :         Options:
                               :         s1, s2 - shapes for checking;
                               :         -op - specifies the type of Boolean operation, for which the validity of shapes should be checked; Should be followed by the operation;
                               :         -se - disables the check of the shapes on small edges;
                               :         -si - disables the check of the shapes on self-interference.
bopargcheck                    : use bopargcheck without parameters to get 
bopbface                       : Splits the face by set of shared edges. Use: bopbface fr cx
bopbsolid                      : Build solids from set of shared faces. Use: bopbsolid sr cx
bopcb                          : Shows information about common blocks. Use: bopcb [#e]
bopcheck                       : use bopcheck Shape [level of check: 0 - 9] [-t]
bopcommon                      : use bopcommon r
bopcurves                      : use bopcurves F1 F2 [-2d/-2d1/-2d2] [-p u1 v1 u2 v2 (to add start points] [-v (for extended output)]
bopcut                         : use bopcut r
bopds                          : Shows the shapes from DS. Use: bopds [v/e/w/f/sh/s/cs/c]
bopfav                         : Shows information about alone vertices for the face. Use: bopfav #f
bopfin                         : Shows IN information for the face. Use: bopfin #f
bopfon                         : Shows ON information for the face. Use: bopfon #f
bopfsc                         : Shows SC information for the face. Use: bopfsc #f
bopfsd                         : Shows SD faces for the face: Use: bopfsd f
bopfuse                        : use bopfuse r
bopimage                       : Shows split parts of the shape. Use: bopimage s
bopindex                       : Gets the index of the shape in the DS. Use: bopindex s
bopinterf                      : Shows interferences of given type. Use: bopinterf type1 type2
bopiterator                    : Shows the pairs of interfered shapes. Use: bopiterator [type1 type2]
bopnews                        : Shows the newly created shapes. Use: bopnews [v,e,f]
boporigin                      : Shows the original shape for the shape. Use: boporigin s
boppb                          : Shows information about pave blocks. Use: boppb [#e]
bopsc                          : Shows the section curves. Use: bopsc [nF1 [nF2]]
bopsd                          : Gets the Same domain shape. Use: bopsd #
bopsection                     : use bopsection r
bopsp                          : Shows the splits of edges. Use: bopsp [#e]
boptions                       : Usage: boptions [-default]
                               :         w/o arguments shows current value of BOP options
                               :         -default - allows setting all options to default values
boptuc                         : use boptuc r
bopwho                         : Shows where the new shape was created. Use: bopwho #
breducetolerance               : use breducetolerance Shape
brunparallel                   : Enables/Disables parallel processing mode.
                               :         Usage: brunparallel 0/1
bsection                       : use bsection r s1 s2 [-n2d/-n2d1/-n2d2] [-na]Builds section between shapes. Options:
                               : -n2d/-n2d1/-n2d2 - disable the PCurve construction;
                               : -na - disables the approximation of the section curves.
bsimplify                      : Enables/Disables the result simplification after BOP
                               :         Usage: bsimplify [-e 0/1] [-f 0/1] [-a tol]
                               :         -e 0/1 - enables/disables edges unification
                               :         -f 0/1 - enables/disables faces unification
                               :         -a tol - changes default angular tolerance of unification algo (accepts value in degrees).
bsplit                         : Builds the result of Split operation. Intersection (bfillds) has to be already performed by this moment.
                               :         Usage: bsplit result [-t]
                               :         Where:
                               :         result - name of the result shape
                               :         -t is the optional parameter for enabling timer and showing elapsed time of the operation
btolx                          : use btolx Shape [minTol=1.e-7]
btuc                           : use btuc r s1 s2
buildbop                       : Builds the result of BOP basing on the GF, thus bbuild command has to be already performed
                               :         The command uses classification approach for building the result of BOP
                               :         (thus it operates on solids only and can be used on open solids):
                               :          - FUSE is built from the faces OUT of all arguments
                               :          - COMMON is built from the faces IN any of the object/tools
                               :          - CUT is built from the objects faces OUT of the tools and tools faces IN the objects.
                               :         Please note that history for solids will not be available.
                               : 
                               :         Usage: buildbop result -o s1 [s2 ...] -t s3 [s4 ...] -op operation (common/fuse/cut/tuc)
                               :         Where:
                               :         result      - result shape of the operation
                               :         s1 s2 s3 s4 - arguments (solids) of the GF operation
                               :         operation   - type of boolean operation
buildpcurvesonplane            : buildpcurvesonplane shape
buseobb                        : Enables/disables the usage of OBB in BOP algorithms
                               :         Usage: buseobb 0 (off) / 1 (on)
cclearrepetitions              : cclearrepetitions [result]
                               :         Clears all previous repetitions of the periodic shape.
checkcurveonsurf               : use checkcurveonsurf shape
clearrepetitions               : clearrepetitions [result]
                               :         Clears all previous repetitions of the periodic shape.
cmakeperiodic                  : cmakeperiodic result [-x/y/z period [-trim first]]
                               :         Make the connected shape periodic in the required directions.
                               :         result        - resulting periodic shape;
                               :         -x/y/z period - option to make the shape periodic in X, Y or Z
                               :                          direction with the given period;
                               :         -trim first   - option to trim the shape to fit the required period,
                               :                         starting the period in first.
cmaterialson                   : cmaterialson result +/- shape
                               :         Returns the original shapes located on the required side of a shape:
                               :         '+' - on a positive side of a shape (containing the shape with orientation FORWARD)
                               :         '-' - on a negative side of a shape (containing the shape with orientation REVERSED).
cperiodictwins                 : cperiodictwins twins shape
                               :         Returns the twins for the shape located on the opposite side of the periodic shape.
crepeatshape                   : crepeatshape result -x/y/z times
                               :         Repeats the periodic connected shape in periodic directions required number of times.
                               :         result       - resulting shape;
                               :         -x/y/z times - direction for repetition and number of repetitions.
edgestofaces                   : edgestofaces faces edges [-a AngTol -s Shared(0/1)]
edgestowire                    : edgestowire wire edges
makeconnected                  : makeconnected result shape1 shape2 ...
                               :         Make the given shapes connected (glued).
makeperiodic                   : makeperiodic result shape [-x/y/z period [-trim first]]
                               :         Make the shape periodic in the required directions.
                               :         result        - resulting periodic shape;
                               :         -x/y/z period - option to make the shape periodic in X, Y or Z
                               :                          direction with the given period;
                               :         -trim first   - option to trim the shape to fit the required period,
                               :                         starting the period in first.
mkvolume                       : make solids from set of shapes.
                               : mkvolume r b1 b2 ... [-c] [-ni] [-ai]
periodictwins                  : periodictwins twins shape
                               :         Returns the twins for the shape located on the opposite side of the periodic shape.
removefeatures                 : removefeatures result shape f1 f2 ... [-parallel]
                               :         Removes user-defined features (faces) from the shape.
                               :         result   - result of the operation;
                               :         shape    - the shape to remove the features from;
                               :         f1, f2   - features to remove from the shape;
                               :         parallel - enables the parallel processing mode.
repeatshape                    : repeatshape result -x/y/z times
                               :         Repeats the periodic shape in periodic directions required number of times.
                               :         result       - resulting shape;
                               :         -x/y/z times - direction for repetition and number of repetitions.
xdistef                        : use xdistef edge face
add                            : add what where
                               :   adds shape "what" to shape "where" 
binrestore                     : alias to readbrep command
binsave                        : binsave shape filename
check                          : check shape1 shape2 ...
complement                     : complement name1 name2 ...
compound                       : compound [name1 name2 ..] compound
countshapes                    : countshapes s; count of shape
discretisation                 : discretisation [nbpoints]
emptycopy                      : emptycopy [copyshape] originalshape
explode                        : explode name [Cd/C/So/Sh/F/W/E/V]
exwire                         : exwire wirename
hlr                            : [no]hlr, rg1, rgn, hid, ang
invert                         : invert name, reverse subshapes
isos                           : isos [name1 ...] [nbisos]
nbshapes                       :  nbshapes s - shows the number of sub-shapes in <s>;
                               :  nbshapes s -t - shows the number of sub-shapes in <s> counting the same sub-shapes with different location as different sub-shapes.
nexplode                       : stable numbered explode for vertex, edge and face: nexplode name [V/E/F]
normals                        : normals shape [Length {10}] [-NbAlongU {1}] [-NbAlongV {1}] [-UseMesh] [-print], display normals
numshapes                      : numshapes s; size of shape
orientation                    : orientation name1 name2.. F/R/E/I
polygons                       : polygons [name1]..., display polygons of shapes if exists
purgemmgt                      : returns the free memory from the system to the memory manager
readbrep                       : readbrep filename shape
                               : Restore the shape from the binary or ASCII format file.
removeinternals                : removeinternals shape [force flag {0/1}]
                               :                      Removes sub-shapes with internal orientation from the shape.
                               : 
                               :                      Force flag disables the check on topological connectivity andremoves all internal sub-shapes
setflags                       : setflags shape_name flag1[flag2...]
                               :  sets flags for shape(free, modified, checked, orientable, closed, infinite, convex, locked), for example <setflags a free> or <setflags a -free> if necessary unflag 
tclean                         : tclean [-force] [-geom] [name1]..., depending on using or not key -geom, 
                               :          -geom  : erase geometry
                               :                   if [-geom] is omitted - erase triangulations and 
                               :                   polygons on triangulations from shapes 
                               :          -force : force delete all representations not relevant to the given shape 
treverse                       : treverse name1 name2 ...
triangles                      : triangles [name1]..., display triangles of shapes if exists
vconn                          : vconn [name1 ...] , edges are colored by number of faces (see vori)
vori                           : vori [name1 ...], edges are colored by orientation (see vconn)
writebrep                      : writebrep shape filename [-binary {0|1}]=0 [-version Version]=4
                               :                          [-triangles {0|1}]=1 [-normals {0|1}]=0
                               : Save the shape in the ASCII (default) or binary format file.
                               :  -binary  write into the binary format (ASCII when unspecified)
                               :  -version a number of format version to save;
                               :           ASCII  versions: 1, 2 and 3    (3 for ASCII  when unspecified);
                               :           Binary versions: 1, 2, 3 and 4 (4 for Binary when unspecified).
                               :  -triangles write triangulation data (TRUE when unspecified).
                               :           Ignored (always written) if face defines only triangulation (no surface).
                               :  -normals include vertex normals while writing triangulation data (FALSE when unspecified).
AddDirectory                   : AddDirectory (DF, entry)
AppendNode                     : AppendNode (DOC FatherEntry childEntry [fatherGUID])
ChangeByteArray                : ChangeByteArray (DF, entry, indx, value )
ChangeExtStrArray              : ChangeExtStrArray (DF, entry, indx, value )
ChangeIntArray                 : ChangeIntArray (DF, entry, indx, value )
ChangeIntPackedMap_Add         : ChangeIntPackedMAp_Add (DF, entry, key[,key [...]] )
ChangeIntPackedMap_AddRem      : ChangeIntPackedMAp_AddRem (DF, entry, key[,key [...]] )
ChangeIntPackedMap_Rem         : ChangeIntPackedMAp_Rem (DF, entry, key[,key [...]] )
ChangeRealArray                : ChangeRealArray (DF, entry, indx, value )
ChildNodeIterate               : ChildNodeIterate Doc TreeNode AllLevels [GUID]
ChildNodeMore                  : ChildNodeMore
ChildNodeNext                  : ChildNodeNext
ChildNodeNextBrother           : ChildNodeNextBrother
ChildNodeValue                 : ChildNodeValue
DetachNode                     : DetachNode (DOC TreeNodeEntry [GUID])
DumpPattern                    : DumpPattern (DF, entry)
DumpRelation                   : DumpRelation (DF, entry)
DumpTriangulation              : DumpTriangulations (DF, entry) - dumps info about triangulation that                     stored in DF in triangulation attribute of a label with the passed entry
GetAsciiString                 : GetAsciiString (DF, entry  )
GetAxis                        : GetAxis (DF, entry, [drawname])
GetBooleanArray                : GetBooleanArray (DF, entry [, guid])
GetBooleanArrayValue           : GetBooleanArrayValue (DF, entry, index)
GetBooleanList                 : GetBooleanList (DF, entry [, guid])
GetByteArray                   : GetByteArray (DF, entry [, guid])
GetByteArrayValue              : GetByteArrayValue (DF, entry, index)
GetComment                     : GetComment (DF, entry)
GetConstraint                  : GetConstraint (DF, entry)
GetExtStringArray              : GetExtStringArray (DF, entry [, guid])
GetExtStringArrayValue         : GetExtStringArrayValue (DF, entry, index)
GetExtStringList               : GetExtStringList (DF, entry [, guid])
GetGeometryType                : GetGeometryType (DF, entry)
GetIntArray                    : GetIntArray (DF, entry [, guid])
GetIntArrayValue               : GetIntArrayValue (DF, entry, index)
GetIntPackedMap                : GetIntPackedMap (DF, entry  )
GetInteger                     : GetInteger (DF, entry, [drawname][, guid])
GetIntegerList                 : GetIntegerList (DF, entry [, guid])
GetNDByte                      : GetNDByte (DF entry key [drawname])
GetNDBytes                     : GetNDBytes (DF entry )
GetNDIntArray                  : GetNDIntArray (DF entry key )
GetNDIntArrays                 : GetNDIntArrays (DF, entry )
GetNDInteger                   : GetNDInteger (DF entry key [drawname])
GetNDIntegers                  : GetNDIntegers (DF, entry )
GetNDReal                      : GetNDReal (DF entry key [drawname])
GetNDRealArray                 : GetNDRealArray (DF entry key )
GetNDRealArrays                : GetNDRealArrays (DF entry )
GetNDReals                     : GetNDReals (DF entry )
GetNDString                    : GetNDString (DF entry key [drawname])
GetNDStrings                   : GetNDStrings (DF entry )
GetPlane                       : GetPlane (DF, entry, [drawname])
GetPoint                       : GetPoint (DF, entry, [drawname])
GetPosition                    : GetPosition (DF, entry, X(out), Y(out), Z(out))
GetReal                        : GetReal (DF, entry, [drawname][, guid])
GetRealArray                   : GetRealArray (DF, entry [, guid])
GetRealArrayValue              : GetRealArrayValue (DF, entry, index)
GetRealList                    : GetRealList (DF, entry [, guid])
GetRefArray                    : GetRefArray (DF, entry [, guid])
GetRefArrayValue               : GetRefArrayValue (DF, entry, index)
GetReference                   : GetReference (DF, entry)
GetReferenceList               : GetReferenceList (DF, entry [, guid])
GetShape2                      : GetShape2 (DF, entry, out_shape )
GetUAttribute                  : GetUAttribute (DF, entry)
GetVariable                    : GetVariable (DF, entry, [isConstant], [units])
InitChildNodeIterator          : InitChildNodeIterator Doc TreeNode AllLevels [GUID]
InsertAfterBooleanList         : InsertAfterBooleanList (DF, entry, index, value )
InsertAfterExtStringList       : InsertAfterExtStringList (DF, entry, index, value )
InsertAfterIntegerList         : InsertAfterIntegerList (DF, entry, index, value )
InsertAfterRealList            : InsertAfterRealList (DF, entry, index, value )
InsertAfterReferenceList       : InsertAfterReferenceList (DF, entry, index, value )
InsertBeforeBooleanList        : InsertBeforeBooleanList (DF, entry, index, value )
InsertBeforeExtStringList      : InsertBeforeExtStringList (DF, entry, index, value )
InsertBeforeIntegerList        : InsertBeforeIntegerList (DF, entry, index, value )
InsertBeforeRealList           : InsertBeforeRealList (DF, entry, index, value )
InsertBeforeReferenceList      : InsertBeforeReferenceList (DF, entry, index, value )
InsertNodeAfter                : InsertNodeAfter (DOC TreeNodeEntry TreeNodeWhichHasToBeAfter [GUID])
InsertNodeBefore               : InsertNodeBefore (DOC TreeNodeEntry TreeNodeWhichHasToBeBefore [GUID])
MakeObjectLabel                : MakeObjectLabel (DF, entry)
NewDirectory                   : NewDirectory (DF, entry)
NewNoteBook                    : NewNoteBook (DF, entry)
NewShape                       : NewShape (DF, entry, [in_shape] )
OpenNode                       : PRIVATE COMMAND FOR TREE BROWSER!
                               : Returns the list of sub-TreeNodes : OpenTreeNode browsername [entry]
PrependNode                    : PrependNode (DOC FatherEntry childEntry [fatherGUID])
RemoveBooleanList              : RemoveBooleanList (DF, entry, index )
RemoveExtStringList            : RemoveExtStringList (DF, entry, index )
RemoveIntegerList              : RemoveIntegerList (DF, entry, index )
RemoveRealList                 : RemoveRealList (DF, entry, index )
RemoveReferenceList            : RemoveReferenceList (DF, entry, index )
RootNode                       : RootNode (DOC TreeNodeEntry [GUID])
Self                           : Self(document, entry)
SetAsciiString                 : SetAsciiString (DF, entry, String  )
SetAxis                        : SetAxis (DF, entry, [drawline])
SetBooleanArray                : SetBooleanArray (DF, entry, [-g Guid,] From, To [, elmt1, elmt2, ...])
SetBooleanArrayValue           : SetBooleanArrayValue (DF, entry, index, value)
SetBooleanList                 : SetBooleanList (DF, entry, [-g Guid,] elmt1, elmt2, ...  )
SetByteArray                   : SetByteArray (DF, entry, isDelta, [-g Guid,] From, To [, elmt1, elmt2, ...])
SetByteArrayValue              : SetByteArrayValue (DF, entry, index, value)
SetComment                     : SetComment (DF, entry, comment)
SetConstraint                  : SetConstraint (DF,entry,keyword,geometrie/value[,geometrie])
SetExtStringArray              : SetExtStringArray (DF, entry, isDelta, [-g Guid,] From, To [, elmt1, elmt2, ...])
SetExtStringArrayValue         : SetExtStringArrayValue (DF, entry, index, value)
SetExtStringList               : SetExtStringList (DF, entry,[-g Guid,] elmt1, elmt2, ...  )
SetGeometry                    : SetGeometry (DF, entry, [type], [shape])
SetIntArray                    : SetIntArray (DF, entry, isDelta, [-g Guid,] From, To [, elmt1, elmt2, ...])
SetIntArrayT                   : SetIntArrayT (DF, entry, isDelta, From, To  )
SetIntArrayValue               : SetIntArrayValue (DF, entry, index, value)
SetIntPHugeMap                 : SetIntPHugeMap (DF, entry, isDelta Num)
SetIntPackedMap                : SetIntPackedMap (DF, entry, isDelta, key1, key2, ...  )
SetInteger                     : SetInteger (DF, entry, value [,guid])
SetIntegerList                 : SetIntegerList (DF, entry, [-g Guid,] elmt1, elmt2, ...  )
SetNode                        : SetNode (DOC Entry [GUID])
SetPattern                     : SetPattern (DF,entry,signature,NSentry[realEntry,intEntry[,NSentry,realEntry,intEntry]])
SetPlane                       : SetPlane (DF, entry, [drawplane])
SetPoint                       : SetPoint (DF, entry, [drawpoint])
SetPosition                    : SetPosition (DF, entry, X, Y, Z)
SetReal                        : SetReal (DF, entry, value [,guid])
SetRealArray                   : SetRealArray (DF, entry, isDelta, [-g Guid,] From, To [, elmt1, elmt2, ...])
SetRealArrayValue              : SetRealArrayValue (DF, entry, index, value)
SetRealList                    : SetRealList (DF, entry, [-g guid,] elmt1, elmt2, ...  )
SetRefArray                    : SetRefArray (DF, entry, [-g Guid,] From, To [, lab1, lab2, ...])
SetRefArrayValue               : SetRefArrayValue (DF, entry, index, value)
SetReference                   : SetReference (DF, entry, reference)
SetReferenceList               : SetReferenceList (DF, entry, [-g Guid,] elmt1, elmt2, ...  )
SetRelation                    : SetRelation (DF, entry, expression, var1[, var2, ...])
SetShape                       : SetShape (DF, entry, drawname)
SetTriangulation               : SetTriangulation (DF, entry, face) - adds label with passed entry to                     DF and put an attribute with the triangulation from passed face
SetUAttribute                  : SetUAttribute (DF, entry, LocalID)
SetVariable                    : SetVariable (DF, entry, isConstant[0/1], units)
TreeBrowse                     : TreeBrowse dfname entry [browsername]
GetName                        : GetNmae (DF, entry [,guid])
SetName                        : SetName (DF, entry, name [,guid])
AddComment                     : AddComment Doc string
Close                          : Close the specific document or all documents
                               : Close DOC [-silent]
                               : Close the specific document.
                               : -silent not raise an exception or print error message for an empty document 
                               : Close *
                               : Close all open documents.
GetStorageFormatVersion        : GetStorageFormatVersion Doc
                               : Alias to StorageFormatVersion
IsInSession                    : IsInSession path
ListDocuments                  : ListDocuments
NewDocument                    : NewDocument docname format
OSDPath                        : OSDPath string
Open                           : Open path docname [-stream] [-skipAttribute] [-readAttribute] [-readPath] [-append|-overwrite]
                               :          The options are:
                               :            -stream : opens path as a stream
                               :            -skipAttribute : class name of the attribute to skip during open, for example -skipTDF_Reference
                               :            -readAttribute : class name of the attribute to read only during open, for example -readTDataStd_Name loads only such attributes
                               :            -append : to read file into already existing document once again, append new attributes and don't touch existing
                               :            -overwrite : to read file into already existing document once again, overwriting existing attributes
Path                           : Path string
PrintComments                  : PrintComments Doc
Save                           : Save
SaveAs                         : SaveAs DOC path [saveEmptyLabels: 0|1] [-stream]
SetStorageFormatVersion        :         : Alias to StorageFormatVersion
StorageFormatVersion           : StorageFormatVersion Doc [Version]
                               : Print or set storage format version within range 2..12
                               : defined by TDocStd_FormatVersion enumeration.
AbortCommand                   : AbortCommand DOC
CommitCommand                  : CommitCommand DOC
Copy                           : Copy DOC entry XDOC xentry
CopyWithLink                   : CopyWithLink DOC entry XDOC xentry
DumpCommand                    : DumpCommand (DOC)
DumpDocument                   : DumpDocument (DOC)
Format                         : Format (DOC, [format])
Main                           : Main (DOC)
NewCommand                     : NewCommand DOC
OpenCommand                    : OpenCommand DOC
Propagate                      : Propagate DOC
Redo                           : Redo DOC (steps = 1)
SetModified                    : SetModified DOC Label1 Label2 ....
StoreTriangulation             : StoreTriangulation [toStore={0|1}] [-normals=off] [-noNormals=on]
                               :  -normals -noNormals write triangulation normals.
                               :  Ignored (always off) if toStore=0 or skipped
                               : Setup BinXCAF/BinOcaf storage drivers to write triangulation
Undo                           : Undo DOC (steps = 1)
UndoLimit                      : UndoLimit DOC (Value), return UndoLimit Undos Redos
UpdateLink                     : UpdateLink DOC [entry]
UpdateXLinks                   : UpdateXLinks DocName DocEntry
XProgress                      : XProgress [+|-t] [+|-c] [+|-g]
                               :          The options are:
                               :            +|-t :  switch on/off output to tcl of Progress Indicator
                               :            +|-c :  switch on/off output to cout of Progress Indicator
                               :            +|-g :  switch on/off graphical mode of Progress Indicator
cleardata                      : mode:a-g-c-p  : Clears all or some data (model, check...)
clearfile                      : Efface la liste d'EvalFile
clearitems                     : Clears all items (selections, dispatches, etc)
count                          : Count : counter [selection]
data                           : Data (DumpModel); whole help : data tout court
dispsel                        : disp:Dispatch sel:Selection  -> Selection Finale de Dispatch
dumpdisp                       : disp:Dispatch   : Affiche le Statut d'un Dispatch
dumpmodif                      : modif:Modifier  : Affiche le Statut d'un Modifier
dumpsel                        : Dump Selection suivi du Nom de la Selection a dumper
dumpshare                      : Dump Share (dispatches, IntParams)
editapply                      : editform [keep] : applies on loaded data
editclear                      : editform [paramname] : clears edition on all or one param
editlist                       : editor or editform : lists defs + values
editload                       : editform [entity-id] : loads from model or an entity
editvalue                      : editform paramname [newval or .] : lists-changes a value
elabel                         : nument:integer   : Displays Label Model of an entity
entity                         : give n0 ou id of entity [+ level]
enum                           : label:string  : Displays entities n0.s of which Label Model ends by..
estatus                        : ent/nument : displays status of an entity
evaladisp                      : mode=[0-3]  disp:Dispatch [givelist]  : Evaluates a Dispatch (on a GiveList)
evalcomplete                   : Evaluation Complete de la Repartition
evaldisp                       : mode=[0-3]  disp:Dispatch  : Evaluates one or more Dispatch(es)
evalfile                       : Evaluation du FileNaming et memorisation
evalsel                        : name:Selection [num/sel]  : Evalue une Selection
filedef                        : defroot:string   : definit File DefaultRoot
fileext                        : extent:string    : definit File Extension
fileprefix                     : prefix:string    : definit File Prefix
fileroot                       : disp:Dispatch  root:string  : definit File Root sur un Dispatch
fromshape                      : shape [level=1]: imported/exported entity (when known)
givecount                      : num/sel [num/sel ...]  : Counts GiveList
givelist                       : num/sel [num/sel ...]  : Evaluates GiveList
givepointed                    : num/sel [num/sel ...]  : GiveList to fill a SelectPointed
giveshort                      : num/sel [num/sel ...]  : GiveList in short form
handler                        : Toggle status catch Handler Error of the session
input                          : sel:Selection genre Deduct ou Extract  input:Selection  : Set Input
itemlabel                      : xxx xxx : liste items having this label
listcount                      : List Counted : counter [selection [nument]]
listitems                      : List Items [label else all]  ->Type,Label[,Name]
listmodif                      : List Final Modifiers
listtypes                      : List nb entities per type. Optional selection name  else all model
makelist                       : listname [givelist] : Makes a List(SelectPointed) from GiveList
modifmove                      : modif:Modifier M(model)/F(file) avant,apres:integer  : Deplace un Modifier (sortie fichier)
modifsel                       : modif:Modifier [sel:Selection]  : Change/Annule Selection de Modifier
newmodel                       : produces a new empty model, for the session
param                          : nompar:string : displays parameter value; + nompar val : changes it
queryparent                    :  give 2 n0s/labels of entities : dad son
remaining                      : options... : Remaining Entities, help complet par  remaining ?
resetapplied                   : modif:Modifier  : Enleve un Modifier de la sortie fichier
runcheck                       : affiche LastRunCheckList (write,modif)
runcopy                        : modif:ModelModifier [givelist] : Run <modif> via TransformStandard option Copy
runonthespot                   : modif:ModelModifier [givelist] : Run <modif> via TransformStandard option OnTheSpot
runtranformer                  : transf:Transformer  : Applique un Transformer
seladd                         : sel:Selection genre Combine  input:Selection  : Add Selection
selmain                        : sel:Selection genre Control  main:Selection  : Set Main Input
selrem                         : sel:Selection genre Combine  input:Selection  : Remove Selection
selsecond                      : sel:Selection genre Control  sec:Selection   : Set Second Input
sentfiles                      : Lists files sent from last Load
setapplied                     : modif:Modifier [name:un item sinon sortie fichier]  : Applique un Modifier
setcontent                     : sel:Selection mode:k ou r  : Restreint contenu du modele
setint                         : name:IntParam   newValue:integer  : Change valeur IntParam
setlist                        : sel:SelectPointed  : edition SelectPointed. tout court pour help
setpointed                     : sel:SelectPointed  : edition SelectPointed. tout court pour help
settext                        : Name:TextParam  newValue:string   : Change valeur TextParam
signature                      : signature name + n0/ident entity
signcase                       : signature : displays possible cases
signtype                       : Sign Type [newone]
sumcount                       : Summary Counted : counter [selection [nument]]
toggle                         : sel:Selection genre Extract  : Toggle Direct/Reverse
tpclear                        : Clears  TransferProcess (READ)
tpcompound                     : name:cstring [givelist] : -> compound with Shapes Root or from givelist
tpdraw                         : [mode:item or root]  num|*  [nomvar] Passes an ITEM to Shape Draw (Start or Result)
tpent                          : [num:integer] Statistics on an entity of the model (READ)
tpitem                         : [num:integer] Statistics on ITEM of transfer (READ)
tproot                         : [num:integer] Statistics on a ROOT of transfert (READ)
tpstat                         : Statistics on TransferProcess (READ)
tptr                           : feeds tr... from tp... (may be incomplete)
trbegin                        : begin-transfer-reader [init]
trcomp                         : results -> 1 compound -> DRAW + name optional
trconnexent                    : name of draw shape : entities -> connected shapes (when known)
trdraw                         : results ->DRAW : all;  or num [name] : from ent.num -> DRAW [name/tread_num]
tread                          : transfers all roots, or num|sel|sel num : entity list, by transfer-reader
trecord                        : record : all root results; or num : for entity n0.num
trimpcomp                      : filename or .  varname  givelist -> one xcompound
trimport                       : filename or .  varname  givelist  -> 1 shape per entity
trsave                         : results ->files : all;  or num [name] : from ent.num -> DRAW [name/tread_num]
trscomp                        : results -> 1 compound -> file + name optional
trstat                         : general statistics;  or num : stats on entity n0 num
trtp                           : feeds commands tp... with results from tr...
twclear                        : Clears  TransferProcess (WRITE)
twitem                         : [num:integer] Statistics on an ITEM of transfer (WRITE)
twmode                         : displays mode transfer write, + num  changes it
twrite                         : shape : transfer write for this shape, AFTER newmodel !
twroot                         : [num:integer] Statistics on a ROOT of transfer (WRITE)
twstat                         : Statistics on TransferProcess (WRITE)
writeall                       : file:string  : Write all model (no split)
writedisp                      : filepattern  disp:Dispatch [givelist]  : Writes Entities by Splitting by a Dispatch
writeent                       : file:string  n1ent n2ent...:integer : Write Entite(s) (no split)
writent                        : file:string  n1ent n2ent...:integer : Write Entite(s) (no split)
writesel                       : file:string sel:Selection : Write Selected (no split)
xinit                          : [norm:string to change norme] reinitialises according to the norm
xload                          : file:string  : Read File -> Load Model
xnorm                          : displays current norm   +norm : changes it
xread                          : file:string  : Read File -> Load Model
xremove                        : nom  : Remove a Control Item de la Session
xrestore                       : filename:string  : restaure items-session
xsave                          : filename:string  : sauve items-session
xsplit                         : [disp:Dispatch  sinon tout]  : Split, la grande affaire !
xstatus                        : Lists XSTEP Status : Version, System Name ...
TPSTAT                         :  
TPSTAT                         :  
brepiges                       : brepiges sh1 [+sh2 [+sh3 ..]] filename.igs
brepiges                       : brepiges sh1 [+sh2 [+sh3 ..]] filename.igs
etest                          : test of eviewer
etest                          : test of eviewer
igesbrep                       : igesbrep [file else already loaded model] [name DRAW]
igesbrep                       : igesbrep [file else already loaded model] [name DRAW]
igesparam                      : igesparam ->list, + name ->one param, + name val->change
igesparam                      : igesparam ->list, + name ->one param, + name val->change
igesread                       : igesread [file else already loaded model] [name DRAW]
igesread                       : igesread [file else already loaded model] [name DRAW]
testreadiges                   : testreadiges [file else already loaded model] [name DRAW]
testreadiges                   : testreadiges [file else already loaded model] [name DRAW]
testwriteiges                  : testwriteiges filename.igs shape
testwriteiges                  : testwriteiges filename.igs shape
tplosttrim                     : number of untrimmed faces during last transfer
tplosttrim                     : number of untrimmed faces during last transfer
countexpected                  : TEST
countexpected                  : TEST
dumpassembly                   : TEST
dumpassembly                   : TEST
stepfileunits                  : stepfileunits name_file
stepfileunits                  : stepfileunits name_file
stepread                       : stepread  [file] [f or r (type of model full or reduced)]
stepread                       : stepread  [file] [f or r (type of model full or reduced)]
steptrans                      : steptrans shape stepax1 stepax2
steptrans                      : steptrans shape stepax1 stepax2
stepwrite                      : stepwrite mode[0-4 afsmw] shape
stepwrite                      : stepwrite mode[0-4 afsmw] shape
testreadstep                   : testreadstep file shape [-stream]
testreadstep                   : testreadstep file shape [-stream]
testwritestep                  : testwritestep filename.stp shape
testwritestep                  : testwritestep filename.stp shape
anaedges                       : nom shape
expwire                        : nom wire [nom face]
fbclose                        : shp sewtoler closetoler [splitclosed [splitopen]] - closes free bounds; use sewtoler <= 0 for shells (no sewing call)
fbprops                        : shp [toler [splitclosed [splitopen]]] - free bounds properties; toler <= 0 or not specified - for shells (no sewing call)
getareacontour                 : wire 
samerange                      : { shape | result curve2d first last newfirst newlast }
ssolid                         : nom shell + nouveau nom solid
CheckAttrs                     : CheckAttrs DocName Lab1 Lab2 
CheckLabel                     : CheckLabel DocName Label 
ClearDF                        : Clears a DF: ClearDF dfname
CopyDF                         : Copies a label: CopyDF dfname1 entry1 [dfname2] entry2
CopyLabel                      : CopyLabel (DOC, from, to)
MakeDF                         : Makes a new DF: MakeDF dfname
MiniDumpDF                     : Mini dump of a DF (with attributes content): DumpDF dfname
SetAccessByEntry               : SetAccessByEntry DOC 1|0
XDumpDF                        : Exented deep dump of a DF (with attributes content): DumpDF dfname
Attributes                     :  Returns the list of label attributes: Attributes DF label
Children                       :  Returns the list of label children: Children DF label
ForgetAll                      : Forgets all attributes from the label: ForgetAll DF Label
ForgetAtt                      : Forgets the specified by guid attribute or type from the label: ForgetAtt DF Label guid_or_type
Label                          : Label DF entry
NewChild                       : NewChild (DF, [tagger])
NewTag                         : NewTag (DF, tagger)
SetEmptyAttribute              : Sets an empty attribute by its type (like TDataStd_Tick): SetEmptyAttribute DF label type
SetTagger                      : SetTagger (DF, entry)
DFBrowse                       : Creates a browser on a df: DFBrowse dfname [browsername]
DFOpenAttribute                : DON'T USE THIS COMMAND RESERVED TO THE BROWSER!
                               : Returns the reference list of an attribute: DFOpenLabel browsername attributeindex
DFOpenAttributeList            : DON'T USE THIS COMMAND RESERVED TO THE BROWSER!
                               : Returns the attribute list of a label: DFOpenLabel browsername label
DFOpenLabel                    : DON'T USE THIS COMMAND RESERVED TO THE BROWSER!
                               : Returns the list of sub-label entries: DFOpenLabel browsername [label]
AbortTran                      : Aborts a transaction on a DF: AbortTran dfname
CommitTran                     : Commits a transaction on a DF with/without delta generation : CommitTran dfname [withDelta]
CurrentTran                    : Returns the current transaction number on a DF : CurrentTran dfname
DFUndo                         :  Undos last DF commit modifications: Undo dfname [withDelta]
OpenTran                       : Opens a transaction on a DF: OpenTran dfname
GetFunction                    : GetFunction (DF, entry, guid(out), failure(out))
SetFunction                    : SetFunction (DF, entry, guid, failure)
AISColor                       : AISColor (DOC, entry, [color])
AISDefaultColor                : AISDefaultColor (DOC, entry)
AISDefaultMaterial             : AISDefaultMaterial (DOC, entry)
AISDefaultTransparency         : AISDefaultTransparency (DOC, entry)
AISDisplay                     : AISDisplay (DOC, entry, [not_update])
AISDriver                      : AISDriver (DOC, entry, [ID]) - returns DriverGUID stored in attribute or sets new one
AISErase                       : AISErase (DOC, entry)
AISHasOwnColor                 : AISHasOwnColor (DOC, entry)  |  AISHasOwnColor return Boolean
AISHasOwnMaterial              : AISHasOwnMaterial (DOC, entry)  |  AISHasOwnMaterial return Boolean
AISHasOwnTransparency          : AISHasOwnTransparency (DOC, entry)  |  AISHasOwnTransparency return Boolean
AISInitViewer                  : AISInitViewer (DOC)
AISMaterial                    : AISMaterial (DOC, entry, [material])
AISMode                        : AISMode (DOC, entry, [Mode])
AISRemove                      : AISRemove (DOC, entry)
AISRepaint                     : update the AIS viewer
AISSelMode                     : AISSelMode (DOC, entry, [SelMode1 SelMode2 ...])
AISSet                         : AISSet (DOC, entry, ID)
AISTransparency                : AISTransparency (DOC, entry, [real])
AISUnset                       : AISUnset (DOC, entry)
AISUpdate                      : AISUpdate (DOC, entry)
batch                          : returns 1 in batch mode
chrono                         : chrono [name action [action...]] 
                               :   Operates named timer.
                               :   Supported actions: reset, start, stop, restart, show, counter [text].
                               :   Without arguments enables / disables global timer for all DRAW commands.
cpulimit                       : cpulimit [nbseconds], no args remove limits
dbreak                         : raises Tcl exception if user has pressed Control-Break key
dchrono                        : see help of chrono command
ddebugtraces                   : ddebugtraces nbTraces
                               : Sets the number of lines for the stack trace within Standard_Failure constructor.
                               : Intended for debug purposes.
decho                          : switch on / off echo of commands to cout; run without args to get help
dlocale                        : set and / or query locate of C subsystem (function setlocale())
dlog                           : manage logging of commands and output; run without args to get help
dparallel                      : dparallel [-occt {0|1}] [-nbThreads Count] [-nbDefThreads Count]
                               : Manages global parallelization parameters:
                               :   -occt         use OCCT implementation or external library (if available)
                               :   -nbThreads    specify the number of threads in default thread pool
                               :   -nbDefThreads specify the upper limit of threads to be used for default thread pool
                               :                 within single parallelization call (should be <= of overall number of threads),
                               :                 so that nested algorithm can also use this pool
dperf                          : dperf [reset] -- show performance counters, reset if argument is provided
dputs                          : dputs [-intense] [-black|-white|-red|-green|-blue|-yellow|-cyan|-magenta]
                               :       [-nonewline] [stdcout|stdcerr] text
                               : Puts text into console output
dsetsignal                     : dsetsignal [{asIs|set|unhandled|unset}=set] [{0|1|default=$CSF_FPE}]
                               :            [-strackTraceLength Length]
                               : Sets OSD signal handler, with FPE option if argument is given.
                               :  -strackTraceLength specifies length of stack trace to put into exceptions redirected from signals.
dtracelevel                    : dtracelevel [trace|info|warn|alarm|fail]
dversion                       : provides information on OCCT build configuration (version, compiler, OS, C library, etc.)
getsourcefile                  : getsourcefile, or getsourcefile command 
help                           : help pattern, or help command string group, to set help
mallochook                     : debug memory allocation/deallocation, w/o args for help
meminfo                        : meminfo [virt|v] [heap|h] [wset|w] [wsetpeak] [swap] [swappeak] [private] : memory counters for this process
spy                            : spy [file], Save commands in file. no file close
wait                           : wait [time(10)], wait time seconds
2dfit                          : 2dfit [view-id]
2dmd                           : 2dmd [view-id], magnify down
2dmu                           : 2dmu [view-id], magnify up
2dpd                           : 2dpd [view-id], panning down
2dpl                           : 2dpl [view-id], panning left
2dpr                           : 2dpr [view-id], panning right
2dpu                           : 2dpu [view-id], panning up
2dzoom                         : 2dzoom [view-id] z, or zoom2d z for all 2d views
av2d                           : , axono and 2d view
axo                            : , One axonometric view. Orientation +X-Y+Z
back                           : , One back view. Orientation -X+Z
bottom                         : , One bottom view. Orientation +X-Y
color                          : color i colorname, define color i
d                              : d [view-id], rotate down
delete                         : delete [view-id]
dflush                         : dflush, flush the viewer
dfont                          : dfont [name size] : set name and size of Draw font, or reset to default
dptv                           : dptv [view-id], dX , dY , dZ
dtext                          : dtext [x y [z]] string
fd                             : fd [view-id], focal down
fit                            : fit [view-id]
focal                          : focal [f]
front                          : , One front view. Orientation +X+Z
fu                             : fu [view-id], focal up
grid                           : grid [stepX(100) [stepY [stepZ]]] / 0
hardcopy                       : hardcopy [file = a4.ps] [view-id = 1] [format = a4]
haxo                           : , One axonometric horizontal view. Orientation +X-Y+Z
hback                          : , One back horizontal view. Orientation -X+Z
hbottom                        : , One bottom horizontal view. Orientation +X-Y
hcolor                         : hcolor icol width gray (< 1, 0 black)
hfront                         : , One front horizontal view. Orientation +X+Z
hleft                          : , One left horizontal view. Orientation -Y+Z
hpers                          : , One perspective horizontal view
hright                         : , One right horizontal view. Orientation +Y+Z
htop                           : , One top horizontal view. Orientation +X+Y
l                              : l [view-id], rotate left
left                           : , One left view. Orientation -Y+Z
md                             : md [view-id], magnify down
mu                             : mu [view-id], magnify up
mu24                           : , 24 views layout
mu4                            : , Four views layout
mu7                            : , Seven views layout
mu8                            : , Seven views layout
pd                             : pd [view-id], panning down
pers                           : , One perspective view
pl                             : pl [view-id], panning left
pr                             : pr [view-id], panning right
ptv                            : ptv [view-id], X , Y , Z
pu                             : pu [view-id], panning up
r                              : r [view-id], rotate right
right                          : , One right view. Orientation +Y+Z
smallview                      :  AXON PERS -2D- +X+Y ...
top                            : , One top view. Orientation +X+Y
u                              : u [view-id], rotate up
v2d                            : , One 2d view
v2d2                           : 2d view on number 2
vaxo                           : vaxo or <A> : Display axonometric view (+X-Y+Z) in the 3D viewer window.
vback                          : vback : Display back view (-X+Z) in the 3D viewer window.
vbottom                        : vbottom : Display bottom view (+X-Y) in the 3D viewer window.
vfront                         : vfront : Display front view (+X+Z) in the 3D viewer window.
view                           : view view-id type X(0) Y(0) W(500) H(500)
vleft                          : vleft : Display left view (-Y+Z) in the 3D viewer window.
vpers                          : , One perspective vertical view
vright                         : vright : Display right view (+Y+Z) in the 3D viewer window.
vtop                           : vtop or <T> : Display top view (+X+Y) in the 3D viewer window.
wclick                         : wait for a mouse click
wzoom                          : wzoom [view-id X1 Y1 X2 Y2]
                               : - fits the contents of a given rectangle into a view window.
                               : - The view window and rectangle corners are specified through the arguments
                               : - or selected interactively by the user if no arguments are given
xwd                            : xwd [id = 1] <filename>.{png|bmp|jpg|gif}
                               : Dump contents of viewer window to PNG, BMP, JPEG or GIF file
zoom                           : zoom [view-id] z, or zoom z for all 3d views
ClearReport                    : Removes all alerts in default printer
CollectMetricMessages          : CollectMetricMessages [-activate {0|1}]
                               :  Start metric collection by 1, stop by 0. Result is placed in metric attributes of message report.
PrintMessenger                 : PrintMessenger
                               : Prints DumpJson information about messenger.
PrintReport                    : PrintReport [-messenger] [-dump] [-dumpJson]
                               : Send report content to default messenger or stream
                               : Output options:
                               :   -messenger Prints the information about report into messenger.
                               :   -dump      Prints Dump information about report.
                               :   -dumpJson  Prints DumpJson information about report.
SendMessage                    : SendMessage text [text ...]
                               :  Sends the text into the messenger.
SetMessagePrinter              : SetMessagePrinter [-type ostream|systemlog|report|draw] [-state {on|off}=on]
                               : Sets or removes the printer in messenger.
                               : Option -type set type of printer. Printers are applied with And combination.
                               : Option -state add or remove printer
SetReportMetric                : SetReportMetric [metric ...] 
                               :  Activate report metrics, deactivate all if there are no parameters.
                               : 
                               : metric is a value of Message_MetricType, e.g. 1 is Message_MetricType_UserTimeCPU
acos                           : acos(x)
asin                           : asin(x)
atan2                          : atan2(x,y)
cos                            : cos(x)
sin                            : sin(x)
sqrt                           : sqrt(x)
tan                            : tan(x)
unit                           : unit value unitfrom unitto
unitconvtoMDTV                 : unitconvtoMDTV real string
unitconvtoSI                   : unitconvtoSI real string
unitparsing                    : unitparsing string [nbiter]
unitsdico                      : unitsdico
2dclear                        : clear display (2d objects)
autodisplay                    : toggle autodisplay [0/1]
beziersmooth                   :  beziersmooth  cname tol deg [-GR -VA -PR] [filename] 
brestore                       : brestore filename name
bsave                          : bsave name filename
clear                          : clear display
copy                           : copy name1 toname1 name2 toname2 ...
datadir                        : datadir [directory]
del                            : unset (remove) variables matched by glob pattern
dgetenv                        : var : get value of environment variable in C subsystem
directory                      : directory [pattern], list draw variables
disp                           : display variables matched by glob pattern
display                        : display [name1 name2 ...], no names display all
dname                          : dname name, print name
don                            : display only variables matched by glob pattern
donly                          : donly [name1 name2 ...], erase and display
draw                           : draw view mode [name1 name2 ...], draw on view with mode
dset                           : var1 value1 vr2 value2 ...
dsetenv                        : var [value] : set (unset if value is empty) environment variable in C subsystem
dtyp                           : dtyp name1 name2
dump                           : dump name1 name2 ...
dval                           : dval name, return value
era                            : erase variables matched by glob pattern
erase                          : erase [name1 name2 ...], no names erase all
isdraw                         : isdraw var, return 1 if Draw value
isprot                         : isprot var, return 1 if Draw var is protected
lastrep                        : lastrep id X Y [Z] b, return name
pick                           : pick id X Y Z b [nowait]
pickf                          : name : extract picked with mouse face as a new variable 
protect                        : protect name ...
renamevar                      : renamevar name1 toname1 name2 toname2 ...
repaint                        : repaint, force redraw
restore                        : restore filename [variablename]
save                           : save variable [filename]
smooth                         : smooth  cname tol [filename] 
unprotect                      : unprotect name ...
depouille                      :  Inclines faces of a shape, dep result shape dirx diry dirz face angle x y x dx dy dz [face angle...]
draft                          :  Compute a draft surface along a shape, 
                               :  draft result shape dirx diry dirz  angle shape/surf/length [-IN/-OUT] [Ri/Ro] [-Internal]
ndepouille                     :  Inclines faces of a shape, dep result shape dirx diry dirz face 0/1 angle x y x dx dy dz [face 0/1 angle...]
dtryload                       : dtryload path : load and unload specified dynamic loaded library
pload                          : pload [[Key1] [Key2] ...]: Loads Draw plugins
pload                          : pload [[Key1] [Key2] ...]: Loads Draw plugins
battencurve                    : battencurve P1 P2 Angle1 Angle2 Heigth BattenName
freeangle                      : freeangle side BattenName
freecurvature                  : freecurvature side  MVCName 
freeslide                      : freeslide BattenName
minvarcurve                    : MVCurve P1 P2 Angle1 Angle2 Heigth MVCName
setangle                       : setangle side angle BattenName 
setcurvature                   : setcurvature side rho MVCName 
setheight                      : setheight height BattenName 
setphysicalratio               : physicalratio ratio MVCName 
setpoint                       : setpoint side point BattenName 
setslide                       : setangle slidingfactor BattenName 
setslope                       : setslope slope BattenName 
bsmooth                        : bsmooth cname tol [-D degree] [fic]
bzsmooth                       : bzsmooth cname tol degree option [fic]
cirtang                        : cirtang cname [-t <Tolerance>] -c <curve> -p <point> -r <Radius>...
gcarc                          : gcarc name seg/cir p1 p2 p3 p4
interpol                       : interpol cname [fic]
lintan                         : lintan lname curve1 curve2 [angle]
tanginterpol                   : tanginterpol curve [p] num_points points [tangents] modifier  p = periodic
cfindp                         : cfindp name view x y index
chgrange                       : chgrange newname curve2d first last  RequestedFirst RequestedLast ]
cmovep                         : cmovep name index dx dy dz
cmovepoint                     : cmovepoint name u dx dy [dz index1 index2]
cmovetangent                   : cmovetangent name u  x y [z] tx ty [tz constraint = 0]
exchuv                         : exchuv name ...
extendcurve                    : extendcurve name point cont [A(fter)/B(efore)]
extendsurf                     : extendsurf name length cont [U/V] [A(fter)/B(efore)]
incdeg                         : incdeg name degree
incudeg                        : incudeg name degree
incvdeg                        : incvdeg name degree
insertknot                     : insertknot name knot [mult = 1] [knot mult ...]
insertpole                     : insertpole name index x y [z] [weight]
insertuknot                    : insertuknot name knot mult
insertvknot                    : insertvknot name knot mult
movecolp                       : movecolp name col dx dy dz
movelaw                        : movelaw name u  x  tx [ constraint = 0]
movep                          : movep name row col dx dy dz
movepoint                      : movepoint name u v dx dy dz [index1u index2u index2v index2v
moverowp                       : moverowp name row dx dy dz
remcolpole                     : remcolpole name index
remknot                        : remknot name index [mult] [tol]
rempole                        : rempole name index
remrowpole                     : remrowpole name index
remuknot                       : remuknot name index [mult] [tol]
remvknot                       : remvknot name index [mult] [tol]
reverse                        : reverse name ... 
segment                        : segment name Ufirst Ulast [tol]
segsur                         : segsur name Ufirst Ulast Vfirst Vlast [Utol [Vtol]]
setknot                        : setknot name index knot [mult]
setnotperiodic                 : setnotperiodic name
setorigin                      : setorigin name knotindex
setperiodic                    : setperiodic name ...
setunotperiodic                : setunotperiodic name ...
setuorigin                     : setuorigin name knotindex
setuperiodic                   : setuperiodic name ...
setvnotperiodic                : setvnotperiodic name ...
setvorigin                     : setvorigin name knotindex
setvperiodic                   : setvperiodic name ...
setweight                      : setweight curve/surf index1 [index2] weight
                               :         changes a weight of a pole of B-spline curve/surface (index2 is useful for surfaces only)
sfindp                         : sfindp name view x y Uindex Vindex
ureverse                       : ureverse name ... 
vreverse                       : vreverse name ... 
2dapprox                       : 2dapprox result nbpoint [curve] [[x] y [x] y...]
2dinterpole                    : 2dinterpole result nbpoint [curve] [[x] y [x] y ...]
2dcvalue                       : 2dcvalue curvename U  X Y [D1X D1Y D2X D2Y]
2dextrema                      : extrema curve curve
2dproj                         : proj curve x y
approxcurve                    : approxcurve [-L] name curve1 [Surf1] [curve2d2 Surf2] [Tol [cont [maxdeg [maxseg]]]] 
approxcurveonsurf              : approxcurveonsurf name curve2d surface [Tol [cont [maxdeg [maxseg]]]] 
bounds                         : bounds S/C/C2d U1 U2 [V1 V2]
canceldenom                    : canceldenom BSpline-Surface UDirection(0/1) VDirection(0/1)
clcurvature                    : clcurvature curvename
compBsplSur                    : BsplSurf1 BSplSurf2
coord                          : coord P x y [z]: set in x y [z] the coordinates of P
cvalue                         : cvalue curvename U  X Y Z [D1X D1Y D1Z D2X D2Y D2Z]
fitcurve                       : fitcurve result  curve [tol [maxdeg [inverse]]]
length                         : length curve [Tol]
localprop                      : localprop curvename U
minmaxcurandinf                : minmaxcurandinf curve
parameters                     : parameters surf/curve X Y [Z] Tol U [V] : {X Y Z} point, {U V} output parameter(s)
radiusmax                      : radiusmax curvename  radius
radiusratio                    : radiusratio curvename ratio
rawcont                        : rawcont curve1 curve2 u1 u2
shcurvature                    : shcurvature curvename
splitc1                        : splitc1 bspline resultinarray(0/1) [tol] [angtol] 
splitc12d                      : splitc12d bspline2d resultinarray(0/1) [tol] [angtol] 
surface_radius                 : surface_radius surface Uvalue <Real> Vvalue <Real> returns min max radius of curvature
svalue                         : svalue surfname U V X Y Z [DUX DUY DUZ DVX DVY DVZ [D2UX D2UY D2UZ D2VX D2VY D2VZ D2UVX D2UVY D2UVZ]]
curveCcontinuity               : curveCcontinuity   order curv1 u1  curv2  u2   [epsnul  [epsC0 [epsC1  [epsC2 ]]]]  
curveGcontinuity               : curveGcontinuity   order  curv1 u1  curv2  u2   [epsnul  [epsG0  [epsG1  [epsG2 [percent  [maxlen ]]]]]] 
surfaceCcontinuity             :  surfaceCcontinuity   order surf1 parU1 parV1 surf2 parU2 parV2  [eps_nul[ epsC0 [epsC1 [epsC2]]]]
surfaceGcontinuity             :  surfaceGcontinuity   order surf1 parU1 parV1 surf2 parU2 parV2  [eps_nul[ epsG0 [epsG1[percent [maxlen]]]]
2dbeziercurve                  : 2dbeziercurve name nbpole pole, [weight]
2dbsplinecurve                 : 2dbsplinecurve name degree nbknots  knot, umult  pole, weight
2dpbsplinecurve                : 2dpbsplinecurve name degree nbknots  knot, umult  pole, weight (periodic)
beziercurve                    : beziercurve name nbpole pole, [weight]
bisec                          : bisec result line/circle/point line/circle/point
bsplinecurve                   : bsplinecurve name degree nbknots  knot, umult  pole, weight
circle                         : circle name x y [z [dx dy dz]] [ux uy [uz]] radius
ellipse                        : ellipse name x y [z [dx dy dz]] [ux uy [uz]] major minor
gproject                       : gproject projectname curve surface [tolerance [maxdist]]
                               :         [-c continuity][-d maxdegree][-s maxsegments][-2d proj2d][-3d proj3d]
                               :         -c continuity  : set curve continuity (C0, C1, C2) for approximation
                               :         -d maxdegree   : set max possible degree of result for approximation
                               :         -s maxsegments : set max value of parametric intervals the projected curve for approximation
                               :         -2d proj2d     : set necessity of 2d results (0 or 1)
                               :         -3d proj3d     : set necessity of 3d results (0 or 1)
hyperbola                      : hyperbola name x y [z [dx dy dz]] [ux uy [uz]] major minor
law                            : law  name degree nbknots  knot, umult  value
line                           : line name pos dir
parabola                       : parabola name x y [z [dx dy dz]] [ux uy [uz]] focal
pbsplinecurve                  : pbsplinecurve name degree nbknots  knot, umult  pole, weight (periodic)
point                          : point name x y [z]
project                        : project : no args to have help
projonplane                    : projonplane r C3d Plane [dx dy dz] [0/1]
to2d                           : to2d c2dname c3d [plane (XOY)]
to3d                           : to3d c3dname c2d [plane (XOY)]
uiso                           : uiso curvename surfacename u
viso                           : viso curvename surfacename v
2ddeviation                    : 2ddeviation result curve [-i U0] [-d N] [-Napprox N] [-Nexact N] [-approxOnly]
                               : -i - sets an initial parameter for computation by iterative method;
                               : -d - sets number of sub-intervals for searching. Default value is 2.
                               : -Napprox - sets number of iteration for approx deviation computing,
                               :            defauilt value is 10-Nexact - sets number of iteration for exact deviation computing,
                               :           defauilt value is 100-approxOnly - to find deviation with approx method only,
                               :               the exact method is used if this parameter is not specified
2dintanalytical                : 2dintanalytical circle1 circle2Intersect circle1 and circle2 using IntAna2d_AnaIntersection.
2dintersect                    : 2dintersect curve1 [curve2] [-tol tol] [-state]
                               : Intersects the given 2d curve(s).If only one curve is given, it will be checked on self-intersection.
                               : Options:
                               :  -tol - allows changing the intersection tolerance (default value is 1.e-3);
                               :  -state - allows printing the intersection state for each point.
crvpoints                      : crvpoints result <curve or wire> deflection
crvtpoints                     : crvtpoints result <curve or wire> deflection angular deflection - tangential deflection points
discrCurve                     : discrCurve polyline curve params
                               : Approximates a curve by a polyline (first degree B-spline).
                               : nbPnts number - creates polylines with the number points
                               : uniform 0 | 1 - creates polyline with equal length segments
getcurvcontinuity              : getcurvcontinuity {curve or 2dcurve}: 
                               :     Returns the continuity of the given curve
intconcon                      : intconcon curve1 curve2Intersect conic curve1 and conic curve2 using IntAna2d_AnaIntersection
intersect                      : intersect result surf1/curv1 surf2 [tolerance]
                               :           intersect result surf1 surf2 [u1 v1 u2 v2] [U1F U1L V1F V1L U2F U2L V2F V2L] [tolerance]
mypoints                       : mypoints result curv deflection
surfpoints                     : surfoints result surf deflection
uniformAbscissa                : uniformAbscissa Curve nbPnt
uniformAbscissaEl              : uniformAbscissaEl maxR minR nbPnt
approxsurf                     : approxsurf name surf [Tol [CnU CnV [degU degV [nmax]]]] 
appsurf                        : appsurf result C1 C2 C3 .....: 
                               :     Create a surface passing through the curves
beziersurf                     : beziersurf name nbupoles nbvpoles pole, [weight]
bsplinesurf                    : bsplinesurf name udegree nbuknots  uknot, umult  vdegree nbvknots vknot, vmult pole, weight
cone                           : cone name [x y z [dx dy dz [ux uy uz]]] semi-angle radius
convert                        : convert result c2d/c3d/surf [qa,c1,s1,s2,s3,s4,po]
convertfrombezier              : convertfrombezier result nbu [nbv] bz1 [bz2 .... bzn] [tol]
cylinder                       : cylinder name [x y z [dx dy dz [ux uy uz]]]  radius
extsurf                        : extsurf name curvename dx dy dz
fillcurves                     : fillcurves result C1 C2 C3 C4 [style 1/2/3]: 
                               :     Create a surface filling frame of 4 curves
getsurfcontinuity              : getsurfcontinuity surface: 
                               :     Returns the continuity of the given surface
offset                         : offset name basename distance [dx dy dz]
partuyau                       : tuyau result Path Curve/Radius [Curve2] [Radius]
                               :  the parametrization of the surface in the V direction will be as the Path
plane                          : plane name [x y z [dx dy dz [ux uy uz]]]
revsurf                        : revsurf name curvename x y z dx dy dz
ruled                          : ruled result C1 C2
sphere                         : sphere name [x y z [dx dy dz [ux uy uz]]]  radius
sweep                          : sweep result [options] path [Surf] curve [Tol [nbsegment]]
                               :  sweep the curve along the path, options are 
                               :  -FX : Tangent and Normal are fixed
                               :  -FR : Tangent and Normal are given by Frenet trihedron 
                               :  -CF : Tangente is given by Frenet, 
                               :      the Normal is computed to minimize the torsion 
                               :  -DX : Tangent and Normal are given by Darboux trihedron 
                               :      <path> have to be a 2d curve,
                               :      <Surf> have to be defined
                               :  -CN dx dy dz : Normal is given by dx dy dz
tobezier                       : tobezier result c2d/c3d/surf [ufirst, ulast / ufirst, ulast, vfirst, vlast]
torus                          : torus name [x y z [dx dy dz [ux uy uz]]]  major minor
trim                           : trim newname name [u1 u2 [v1 v2] [usense=1 vsense=1]]
                               : Creates either a new trimmed curve from a curve
                               : or a new trimmed surface in u and v from a surface.
                               : Removes trim when called without arguments.
                               : - u1 u2   lower and upper parameters of trimming on U direction
                               : - v1 v2   lower and upper parameters of trimming on V direction
                               : - usense vsense   senses on U and V directions: 1 - true, 0 - false;
                               :             Senses are used for the construction only if the surface is periodic
                               :             in the corresponding parametric direction, and define the available part of the surface
trimu                          : trimu newname name u1 u2 [usense=1]
                               : Creates a u-trimmed surface.
                               : - u1 u2  lower and upper parameters of trimming on U direction
                               : - usense sense on U direction: 1 - true, 0 - false;
                               :             usense is used for the construction only if the surface is u-periodic
                               :             in the u parametric direction, and define the available part of the surface
trimv                          : trimv newname name v1 v2 [vsense=1]
                               : Creates a v-trimmed surface.
                               : - u1 u2  lower and upper parameters of trimming on V direction
                               : - vsense sense on V direction: 1 - true, 0 - false;
                               :             vsense is used for the construction only if the surface is v-periodic
                               :             in the v parametric direction, and define the available part of the surface
tuyau                          : tuyau [-NS] result Path Curve/Radius [Curve2] [Curve3] ... [Radius]
                               :  the option -NS is used only with 2 sections.
                               :  With it, <result> is going from the first section to the last section 
                               :  Without, <result> is a pipe by evolutive section 
upbsplinesurf                  : bsplinesurf name udegree nbuknots  uknot, umult  vdegree nbvknots vknot, vmult pole, weight
uvpbsplinesurf                 : bsplinesurf name udegree nbuknots  uknot, umult  vdegree nbvknots vknot, vmult pole, weight
vpbsplinesurf                  : bsplinesurf name udegree nbuknots  uknot, umult  vdegree nbvknots vknot, vmult pole, weight
circ2d3Tan                     : circ2d3Tan cname {qcicrle1|qlin1|point1} {qcicrle2|qlin2|point2} {qcicrle3|qlin3|point3} [tolerance]
                               : Creates 2d circles tangent to 3 arguments. The arguments are points, lines or circles.
                               : Possible arguments combinations:
                               :            <qcircle, qcircle, qcircle>,
                               :            <qcircle, qcircle, qlin>,
                               :            <qcircle, qcircle, point>,
                               :            <qcircle, qlin, qlin>,
                               :            <qcircle, qlin, point>,
                               :            <qcircle, qlin, qlin>,
                               :            <qcircle, point, point>,
                               :            <qlin, qlin, qlin>,
                               :            <qlin, qlin, point>,
                               :            <qlin, point, point>,
                               :            <point, point, point>.
qcircle                        : qcircle name {x y [ux uy] radius} [-unqualified|-enclosing|-enclosed|-outside|-noqualifier]
                               : Creates qualified circle.
qline                          : qline name x y dx dy [-unqualified|-enclosing|-enclosed|-outside|-noqualifier]
                               : Creates qualified line.
2dlmirror                      : lmirror name [names...] x y dx dy
2dpmirror                      : pmirror name [names...] x y
2dpscale                       : pscale name [names...] x y s
2drotate                       : rotate name [names...] x y dx dy  angle
2dtranslate                    : translate name [names...] dx dy
lmirror                        : lmirror name [names...] x y z dx dy dz
pmirror                        : pmirror name [names...] x y z
pscale                         : pscale name [names...] x y z s
rotate                         : rotate name [names...] x y z dx dy dz angle
smirror                        : smirror name [names...] x y z dx dy dz
translate                      : translate name [names...] dx dy dz
lprops                         : lprops name [x y z] [-skip] [-full] [-tri]: compute linear properties
sprops                         : sprops name [epsilon] [x y z] [-skip] [-full] [-tri]:
                               :   compute surfacic properties
vprops                         : vprops name [epsilon] [c[losed]] [x y z] [-skip] [-full] [-tri]:
                               :   compute volumic properties
vpropsgk                       : vpropsgk name epsilon closed span mode [x y z] [-skip] : compute volumic properties
generated                      : generated generated_shapes history shape
                               :         Returns the shapes Generated from the given shape in the given history
isdeleted                      : isdeleted history shape
                               :         Checks if the given shape has been deleted in the given history
modified                       : modified modified_shapes history shape
                               :         Returns the shapes Modified from the given shape in the given history
savehistory                    : savehistory name
                               :         Saves the history from the session into a drawable object with the name <name>.
setfillhistory                 : Controls the history collection by the algorithms and its saving into the session after algorithm is done.
                               :         Usage: setfillhistory [flag]
                               :         w/o arguments prints the current state of the option;
                               :         flag == 0 - history will not be collected and saved;
                               :         flag != 0 - history will be collected and saved into the session (default).
jsasync                        : jsasync command ...
                               : Run Tcl command asynchronously.
jsdownload                     : jsdownload filePath [fileName]
                               : Download file from emulated file system
                               :   filePath file path within emulated file system to download;
                               :   fileName file name to download.
jsupload                       : jsupload fileUrl1 [-path filePath1] [fileUrl2 [-path filePath2]] ...
                               : Upload files to emulated file system
                               :   fileUrl  URL on server or . to show open file dialog;
                               :   filePath file path within emulated file system to create.
XAttributeValue                : Doc label #attribute: internal command for browser
mtmAbort                       :                           aborts last opened transaction
mtmAdd                         :      <document name>      adds a document to the transactions' manager
mtmCommit                      :      [<transaction name>] commits last opened transaction
mtmCreate                      :      [undo limit]         creates new new multiple transactions' manager
mtmDump                        :                           dumps state of the multiple transactions' manager
mtmNestedMode                  :      [0/1]                sets nested mode if 1 and usets if 0 (default 0)
mtmOpen                        :                           opens new transaction
mtmRedo                        :                           redos last transaction
mtmRemove                      :      <document name>      removes a document from the transactions' manager
mtmUndo                        :                           undos last transaction
MemLeakTest                    : MemLeakTest
correctnormals                 : correctnormals shape
incmesh                        : incmesh Shape LinDefl [-angular Angle]=28.64 [-prs]
                               :   [-relative {0|1}]=0 [-parallel {0|1}]=0 [-min Size]
                               :   [-algo {watson|delabella}]=watson
                               :   [-di Value] [-ai Angle]=57.29
                               :   [-int_vert_off {0|1}]=0 [-surf_def_off {0|1}]=0 [-adjust_min {0|1}]=0
                               :   [-force_face_def {0|1}]=0 [-decrease {0|1}]=0
                               : Builds triangular mesh for the shape.
                               :  LinDefl         linear deflection to control mesh quality;
                               :  -angular        angular deflection for edges in deg (~28.64 deg = 0.5 rad by default);
                               :  -prs            apply default meshing parameters for visualization purposes
                               :                  (20 deg angular deflection, 0.001 of bounding box linear deflection);
                               :  -relative       notifies that relative deflection is used (FALSE by default);
                               :  -parallel       enables parallel execution (FALSE by default);
                               :  -algo           changes core triangulation algorithm to one with specified id (watson by default);
                               :  -min            minimum size parameter limiting size of triangle's edges to prevent sinking
                               :                  into amplification in case of distorted curves and surfaces;
                               :  -di             linear deflection used to tessellate the face interior;
                               :  -ai             angular deflection inside of faces in deg (~57.29 deg = 1 rad by default);
                               :  -int_vert_off   disables insertion of internal vertices into mesh (enabled by default);
                               :  -surf_def_off   disables control of deflection of mesh from real surface (enabled by default);
                               :  -adjust_min     enables local adjustment of min size depending on edge size (FALSE by default);
                               :  -force_face_def disables usage of shape tolerances for computing face deflection (FALSE by default);
                               :  -decrease       enforces the meshing of the shape even if current mesh satisfies the new criteria
                               :                  (FALSE by default).
mperror                        : use mperror
mpgetdefaultname               : use mpgetdefaultname
mpgetfunctionname              : use mpgetfunctionname
mpincmesh                      : use mpincmesh
mpnames                        : use mpnames
mpparallel                     : mpparallel [toTurnOn] : show / set multi-threading flag for incremental mesh
mpsetdefaultname               : use mpsetdefaultname
mpsetfunctionname              : use mpsetfunctionname
tessellate                     : Builds triangular mesh for the surface, run w/o args for help
tri2d                          : tri2d facename
triarea                        : shape [eps]  (computes triangles and surface area)
tricheck                       : shape [-small]  (checks triangulation of shape);
                               : "-small"-option allows finding triangles with small area
triepoints                     : triepoints shape1 [shape2 ...]
trinfo                         : trinfo shapeName [-lods], print triangles information on objects
                               : -lods Print detailed LOD information
trlateload                     : trlateload shapeName
                               :   [-load {-1|Index|ALL}=-1] [-unload {-1|Index|ALL}=-1]
                               :   [-activate Index] [-activateExact Index]
                               :   [-loadSingle {-1|Index}=-1] [-loadSingleExact {Index}=-1]
                               : Interaction with deferred triangulations.
                               :   '-load'            - load triangulation (-1 - currently active one, Index - with defined index,
                               :                      ALL - all available ones)
                               :   '-unload'          - unload triangulation (-1 - currently active one, Index - with defined index,
                               :                      ALL - all available ones)
                               :   '-activate'        - activate triangulation with defined index. If it doesn't exist -
                               :                      activate the last available triangulation.
                               :   '-activateExact'   - activate exactly triangulation with defined index or do nothing.
                               :   '-loadSingle'      - make loaded and active ONLY specified triangulation (-1 - currently active one,
                               :                      Index - with defined index or last available if it doesn't exist).
                               :                      All other triangulations will be unloaded.
                               :   '-loadSingleExact' - make loaded and active ONLY exactly specified triangulation. All other triangulations
                               :                      will be unloaded. If triangulation with such Index doesn't exist do nothing
trmergenodes                   : trmergenodes shapeName
                               :   [-angle Angle] [-tolerance Value] [-oneFace Result]
                               : Merging nodes within triangulation data.
                               :   -angle     merge angle upper limit in degrees; 45 when unspecified
                               :   -tolerance linear tolerance to merge nodes; 0.0 when unspecified
                               :   -oneFace   create a new single Face with specified name for the whole triangulation
veriftriangles                 : veriftriangles name, verif triangles
wavefront                      : wavefront name
SetNDataBytes                  : SetNDataBytes (DF, entry, NumPairs, key1, val1, ...  )
SetNDataIntArrays              : SetNDataIntArrays (DF entry entry  key NumOfArrElems val1 val2...  )
SetNDataIntArrays2             : SetNDataIntArrays2 (DF entry entry  key NumOfArrElems)
SetNDataIntegers               : SetNDataIntegers (DF, entry, NumPairs, key1, val1, ...  )
SetNDataIntegers2              : SetNDataIntegers2 (DF, entry, NumPair  )
SetNDataRealArrays             : SetNDataRealArrays (DF entry key NumOfArrElems val1 val2...  )
SetNDataReals                  : SetNDataReals (DF, entry, NumPairs, key1, val1, ...  )
SetNDataStrings                : SetNDataStrings (DF, entry, NumPairs, key1, val1, ...  )
ArgsSelection                  : ArgsSelection DF entry
Ascendants                     : Ascendants df shape [trans]
Attachment                     : Attachment DF entry
CheckNSIter                    : CheckNSIter df entry shape new[1|0]
Collect                        : Collect  df entry [onlymodif 0/1]
CurrentShape                   : Currentshape df entry [drawname]
Descendants                    : Descendants  df shape [trans]
DumpSelection                  : DumpSelected DF entry
ExploreShape                   : ExploreShape df entry res [trans]
GeneratedShape                 : Generatedshape df shape Generationentry [drawname]
GetCreationEntry               : GetCreationEntry df shape
GetEntry                       : GetEntry df shape
GetShape                       : GetShape df entry [drawname]
ImportShape                    : ImportShape Doc Entry Shape [Name]
InitialShape                   : InitialShape df shape res
NamedShape                     : NamedShape df shape
SelectGeometry                 : SelectGeometry DF entry shape [context]
SelectShape                    : SelectShape DF entry shape [context [Orient]]
SolveSelection                 : DumpSelection DF entry
CheckSame                      : CheckSame (Shape1 Shape2 ExploMode[F|E|V])
CopyShape                      : CopyShape (Shape1 [Shape2] ...)
CopyTool                       : CopyTool Shape1 [Shape2] ...
AddBox                         : AddBox Doc dx dy dz
AddCommon                      : AddCommon Doc Object Tool
AddCut                         : AddCut Doc Object Tool
AddCyl                         : AddCyl Doc Radius Height Axis
AddDriver                      : AddDriver Doc Name [Box|Sph|Cyl|Cut|Fuse|Prism|Revol|PTxyz|PTALine|PRLine|PMirr|Fillet|Attach|XAttach]
AddFillet                      : AddFillet Doc Object Radius Path [SurfaceType(0-Rational;1-QuasiAngular;2-Polynomial)]
AddFunction                    : AddFunction D ObjEntry FunName[Box|Sph|Cyl|Cut|Fuse|Prism|Revol|PMove|Fillet|Attach|XAttach]
AddFuse                        : AddFuse Doc Object Tool
AddLine3D                      : AddLine3D Doc CurveType(0|1) Pnt1 Pnt2 [Pnt3 [Pnt4 [...]]]
AddObject                      : AddObject D
AddPoint                       : AddPoint Doc x y z
AddPointRlt                    : AddPointRlt Doc RefPntObj dx dy dz
AddPrism                       : AddPrism Doc BasisLabel Height Reverse(0/1) 
AddRevol                       : AddRevol Doc BasisLabel  AxisLabel [Angle [Reverse(0/1)]] 
AddSection                     : AddSection Doc Object Tool
AddSphere                      : AddSphere Doc CenterLabel Radius 
AttachShape                    : AttachShape Doc Shape Context [Container [KeepOrientation [Geometry]]]
BoxDX                          : BoxDX Doc BoxLabel NewDX
BoxDY                          : BoxDY Doc BoxLabel NewDY
BoxDZ                          : BoxDZ Doc BoxLabel NewDZ
CheckLogBook                   : CheckLogBook Doc
ComputeFun                     : ComputeFun Doc FunLabel
CylRad                         : CylRad Doc CylLabel NewRad
InitLogBook                    : InitLogBook Doc
PMirror                        : PMirror Doc ShapeEntry PlaneObj
PRotateRoundLine               : PRotateRoundLine Doc ShapeEntry Line Angle
PTranslateAlongLine            : PTranslateAlongLine Doc ShapeEntry  Line off
PTranslateDXYZ                 : PTranslateDXYZ Doc ShapeEntry dx dy dz
PntOffset                      : PntOffset Doc PntLabel newDX|skip newDY|skip newDZ|skip
PrismHeight                    : PrismHeight Doc PrismLabel NewHeight
RevolutionAngle                : RevolutionAngle Doc RevolutionLabel NewAngle
SolveFlatFrom                  : SolveFlatFrom Doc FistAuxObjLabel
SphereRadius                   : SphereRadius Doc SphereLabel NewRadius
TestMultipleSelection          : TestMultipleSelection Doc ObjectLabel [Orientation [Xselection [Geometry]]]
TestSingleSelection            : TestSingleSelection Doc ObjectLabel [Orientation [Xselection [Geometry]]]
XAttachShape                   : XAttachShape Doc Shape Context [KeepOrientation [Geometry]]
addpolygonnode                 : addpolygonnode polygon3d(2d) x y [z]
polygon2d                      : polygon2d name nbnodes x1 y1  ...
polygon3d                      : polygon3d name nbnodes x1 y1 z1  ...
polygonprops                   : Computes area and perimeter of 2D-polygon. Run "polygonprops" w/o any arguments to read help.
polytr                         : polytr name nbnodes nbtri x1 y1 z1 ... n1 n2 n3 ...
shnodes                        : shnodes name
shtriangles                    : shtriangles name
box                            : box name [dx dy dz] [x y z dx dy dz]
                               :            [-min x y z] [-size dx dy dz] [-max x y z]
                               :            [-dir x y z -xdir x y z] [-preview]
                               : Construct axes-aligned box and put result into 'name' variable
                               :  -min   box lower corner, origin; (0,0,0) by default
                               :  -size  box dimensions   (alternative to -max)
                               :  -max   box upper corner (alternative to -size)
                               :  -dir   main direction of coordinate system (DZ by default)
                               :  -xdir  x direction of coordinate system (DX by default)
                               :  -preview non-solid shape will be created (vertex, edge, rectangle or box);
                               :           otherwise, return NULL shape in case of zero box dimension.
pcone                          : pcone name [plane(ax2)] R1 R2 H [angle]
                               : Construct a cone, part cone or conical frustum and put result into 'name' variable.
                               : Parameters of the cone :
                               : - plane  coordinate system for the construction of the cone
                               : - R1     cone bottom radius
                               : - R2     cone top radius
                               : - H      cone height
                               : - angle  angle to create a part cone
pcylinder                      : pcylinder name [plane(ax2)] R H [angle]
                               : Construct a cylinder and put result into 'name' variable.
                               : Parameters of the cylinder :
                               : - plane coordinate system for the construction of the cylinder
                               : - R     cylinder radius
                               : - H     cylinder height
                               : - angle cylinder top radius
psphere                        : psphere name [plane(ax2)] R [angle1 angle2] [angle]
                               : Construct a sphere, spherical segment or spherical wedge and put result into 'name' variable.
                               : Parameters of the sphere :
                               : - plane  coordinate system for the construction of the sphere
                               : - R      sphere radius
                               : - angle1 first angle to create a spherical segment  [-90; 90]
                               : - angle2 second angle to create a spherical segment [-90; 90]
                               : - angle  angle to create a spherical wedge
ptorus                         : ptorus name [plane(ax2)] R1 R2 [angle1 angle2] [angle]
                               : Construct a torus or torus segment and put result into 'name' variable.
                               : Parameters of the torus :
                               : - plane  coordinate system for the construction of the torus
                               : - R1     distance from the center of the pipe to the center of the torus
                               : - R2     radius of the pipe
                               : - angle1 first angle to create a torus ring segment
                               : - angle2 second angle to create a torus ring segment
                               : - angle  angle to create a torus pipe segment
wedge                          : wedge name [Ox Oy Oz Zx Zy Zz Xx Xy Xz] dx dy dz ltx / xmin zmin xmax zmax
checkMultilineStrings          :   Compares two strings.
                               :   Logically splits the strings to lines by the new line characters.
                               :   Outputs the first different lines.
                               : 
                               :   Use: checkMultilineStrings <string_1> <string_2>
checkcolor                     :   Check pixel color.
                               :   Use: checkcolor x y red green blue
                               :   x y - pixel coordinates
                               :   red green blue - expected pixel color (values from 0 to 1)
                               :   Function check color with tolerance (5x5 area)
checkcolor                     :   Check pixel color.
                               :   Use: checkcolor x y red green blue
                               :   x y - pixel coordinates
                               :   red green blue - expected pixel color (values from 0 to 1)
                               :   Function check color with tolerance (5x5 area)
checkdump                      :   Procedure includes command to parse output dump and compare it with reference values.
                               : 
                               :   Use: checkdump shapename [options...]
                               :   Allowed options are:
                               :     -name NAME: list of parsing parameters (e.g. Center, Axis, etc)
                               :     -ref VALUE: list of reference values for each parameter in NAME 
                               :     -eps EPSILON: the epsilon defines relative precision of computation
checkfaults                    :   Compare faults number of given shapes.
                               : 
                               :   Use: checkfaults shape source_shape [ref_value=0]
checkfreebounds                :   Compare number of free edges with ref_value
                               : 
                               :   Use: checkfreebounds shape ref_value [options...]
                               :   Allowed options are:
                               :     -tol N: used tolerance (default -0.01)
                               :     -type N: used type, possible values are "closed" and "opened" (default "closed")
checkgravitycenter             :   Compare Center Of Gravity with given reference data
                               : 
                               :   Use: checkgravitycenter shape prop_type x y z tol
checklength                    :   Procedure includes commands to compute length of input curve.
                               : 
                               :   Use: checklength curvename [options...]
                               :   Allowed options are:
                               :     -l LENGTH: command length, computes the length of input curve with precision of computation
                               :     -eps EPSILON: the epsilon defines relative precision of computation
                               :     -equal CURVE: compare length of input curves. Puts error if its are not equal
                               :     -notequal CURVE: compare length of input curves. Puts error if its are equal
checkmaxtol                    :   Returns max tolerance of the shape and prints error message if specified
                               :   criteria are not satisfied.
                               : 
                               :   Use: checkmaxtol shape [options...]
                               : 
                               :   Options specify criteria for checking the maximal tolerance value:
                               :     -ref <value>: check it to be equal to reference value.
                               :     -min_tol <value>: check it to be not greater than specified value.
                               :     -source <list of shapes>: check it to be not greater than 
                               :             maximal tolerance of specified shape(s)
                               :     -multi_tol <value>: additional multiplier for value specified by -min_tol 
                               :                or -shapes options.
checknbshapes                  :   Compare number of sub-shapes in "shape" with given reference data
                               : 
                               :   Use: checknbshapes shape [options...]
                               :   Allowed options are:
                               :     -vertex N
                               :     -edge N
                               :     -wire N
                               :     -face N
                               :     -shell N
                               :     -solid N
                               :     -compsolid N
                               :     -compound N
                               :     -shape N
                               :     -t: compare the number of sub-shapes in "shape" counting
                               :         the same sub-shapes with different location as different sub-shapes.
                               :     -m msg: print "msg" in case of error
                               :     -ref [nbshapes a]: compare the number of sub-shapes in "shape" and in "a".
                               :                        -vertex N, -edge N and other options are still working.
checkplatform                  :   Return name of current platform if no options are given.
                               : 
                               :   Use: checkplatform [options...]
                               :   Allowed options are:
                               :     -windows : return 1 if current platform is 'Windows', otherwise return 0
                               :     -linux   : return 1 if current platform is 'Linux', otherwise return 0
                               :     -osx     : return 1 if current platform is 'MacOS X', otherwise return 0
                               : 
                               :   Only one option can be used at once.
                               :   If no option is given, procedure will return the name of current platform.
checkpoint                     :   Compare two 3D points with given tolerance
                               :   Use: checkpoint name {valueX valueY valueZ} {expectedX expectedY expectedZ} tolerance
checkprops                     :   Procedure includes commands to compute length, area and volume of input shape.
                               : 
                               :   Use: checkprops shapename [options...]
                               :   Allowed options are:
                               :     -l LENGTH: command lprops, computes the mass properties of all edges in the shape with a linear density of 1
                               :     -s AREA: command sprops, computes the mass properties of all faces with a surface density of 1 
                               :     -v VOLUME: command vprops, computes the mass properties of all solids with a density of 1
                               :     -eps EPSILON: the epsilon defines relative precision of computation
                               :     -deps DEPSILON: the epsilon defines relative precision to compare corresponding values
                               :     -equal SHAPE: compare area\volume\length of input shapes. Puts error if its are not equal
                               :     -notequal SHAPE: compare area\volume\length of input shapes. Puts error if its are equal
                               :     -skip: count shared shapes only once, skipping repeatitions
                               :   Options -l, -s and -v are independent and can be used in any order. Tolerance epsilon is the same for all options.
checkreal                      :   Compare value with expected
                               :   Use: checkreal name value expected tol_abs tol_rel
checktrinfo                    :   Compare maximum deflection, number of nodes and triangles in "shape" mesh with given reference data
                               : 
                               :   Use: checktrinfo shapename [options...]
                               :   Allowed options are:
                               :     -face [N]: compare current number of faces in "shapename" mesh with given reference data.
                               :                If reference value N is not given and current number of faces is equal to 0
                               :                procedure checktrinfo will print an error.
                               :     -empty[N]: compare current number of empty faces in "shapename" mesh with given reference data.
                               :                If reference value N is not given and current number of empty faces is greater that 0
                               :                procedure checktrinfo will print an error.
                               :     -tri [N]:  compare current number of triangles in "shapename" mesh with given reference data.
                               :                If reference value N is not given and current number of triangles is equal to 0
                               :                procedure checktrinfo will print an error.
                               :     -nod [N]:  compare current number of nodes in "shapename" mesh with given reference data.
                               :                If reference value N is not givenand current number of nodes is equal to 0
                               :                procedure checktrinfo will print an error.
                               :     -defl [N]: compare current value of maximum deflection in "shapename" mesh with given reference data
                               :                If reference value N is not given and current maximum deflection is equal to 0
                               :                procedure checktrinfo will print an error.
                               :     -max_defl N:     compare current value of maximum deflection in "shapename" mesh with max possible value
                               :     -tol_abs_tri N:  absolute tolerance for comparison of number of triangles (default value 0)
                               :     -tol_rel_tri N:  relative tolerance for comparison of number of triangles (default value 0)
                               :     -tol_abs_nod N:  absolute tolerance for comparison of number of nodes (default value 0)
                               :     -tol_rel_nod N:  relative tolerance for comparison of number of nodes (default value 0)
                               :     -tol_abs_defl N: absolute tolerance for deflection comparison (default value 0)
                               :     -tol_rel_defl N: relative tolerance for deflection comparison (default value 0)
                               :     -ref [trinfo a]: compare deflection, number of triangles and nodes in "shapename" and in "a"
checkview                      :   Display shape in selected viewer.
                               : 
                               :   Use: checkview [options...]
                               :   Allowed options are:
                               :     -display shapename: display shape with name 'shapename'
                               :     -3d: display shape in 3d viewer
                               :     -2d [ v2d / smallview ]: display shape in 2d viewer (default viewer is a 'smallview')
                               :     -vdispmode N: it is possible to set vdispmode for 3d viewer (default value is 1)
                               :     -screenshot: procedure will try to make screenshot of already created viewer
                               :     -path <path>: location of saved screenshot of viewer
                               : 
                               :     Procedure can check some property of shape (length, area or volume) and compare it with some value N:
                               :       -l [N]
                               :       -s [N]
                               :       -v [N]
                               :     If current property is equal to value N, shape is marked as valid in procedure.
                               :     If value N is not given procedure will mark shape as valid if current property is non-zero.
                               :     -with {a b c}: display shapes 'a' 'b' 'c' together with 'shape' (if shape is valid)
                               :     -otherwise {d e f}: display shapes 'd' 'e' 'f' instead of 'shape' (if shape is NOT valid)
                               :     Note that one of two options -2d/-3d is required.
test                           :   Run specified test case
                               :   Use: test group grid casename [options...]
                               :   Allowed options are:
                               :   -echo: all commands and results are echoed immediately,
                               :          but log is not saved and summary is not produced
                               :          It is also possible to use "1" instead of "-echo"
                               :          If echo is OFF, log is stored in memory and only summary
                               :          is output (the log can be obtained with command "dlog get")
                               :   -outfile filename: set log file (should be non-existing),
                               :          it is possible to save log file in text file or
                               :          in html file(with snapshot), for that "filename"
                               :          should have ".html" extension
                               :   -overwrite: force writing log in existing file
                               :   -beep: play sound signal at the end of the test
                               :   -errors: show all lines from the log report that are recognized as errors
                               :          This key will be ignored if the "-echo" key is already set.
testdiff                       :   Compare results of two executions of tests (CPU times, ...)
                               :   Use: testdiff dir1 dir2 [groupname [gridname]] [options...]
                               :   Where dir1 and dir2 are directories containing logs of two test runs.
                               :   dir1 (A) should point to NEW tests results to be verified and dir2 (B) to REFERENCE results.
                               :   Allowed options are:
                               :   -image [filename]: compare only images and save its in specified file (default 
                               :                    name is <dir1>/diffimage-<dir2>.log)
                               :   -cpu [filename]: compare only CPU and save it in specified file (default 
                               :                    name is <dir1>/diffcpu-<dir2>.log)
                               :   -memory [filename]: compare only memory and save it in specified file (default 
                               :                    name is <dir1>/diffmemory-<dir2>.log)
                               :   -save filename: save resulting log in specified file (default name is
                               :                   <dir1>/diff-<dir2>.log); HTML log is saved with same name
                               :                   and extension .html
                               :   -status {same|ok|all}: filter cases for comparing by their status:
                               :           same - only cases with same status are compared (default)
                               :           ok   - only cases with OK status in both logs are compared
                               :           all  - results are compared regardless of status
                               :   -verbose level: 
                               :           1 - output only differences 
                               :           2 - output also list of logs and directories present in one of dirs only
                               :           3 - (default) output also progress messages 
                               :   -highlight_percent value: highlight considerable (>value in %) deviations
                               :                             of CPU and memory (default value is 5%)
testfile                       :   Checks specified data files for putting them into the test data files repository.
                               : 
                               :   Use: testfile filelist
                               : 
                               :   Will report if:
                               :   - data file (non-binary) is in DOS encoding (CR/LF)
                               :   - same data file (with same or another name) already exists in the repository
                               :   - another file with the same name already exists 
                               :   Note that names are considered to be case-insensitive (for compatibility 
                               :   with Windows).
                               : 
                               :   Unless the file is already in the repository, tries to load it, reports
                               :   the recognized file format, file size, number of faces and edges in the 
                               :   loaded shape (if any), information contained its triangulation, and makes 
                               :   snapshot (in the temporary directory).
                               : 
                               :   Finally it advises whether the file should be put to public section of the 
                               :   repository.
                               : 
                               :   Use: testfile -check
                               : 
                               :   If "-check" is given as an argument, then procedure will check files already 
                               :   located in the repository (for possible duplicates and for DOS encoding).
testgrid                       :   Run all tests, or specified group, or one grid
                               :   Use: testgrid [groupmask [gridmask [casemask]]] [options...]
                               :   Allowed options are:
                               :   -exclude N: exclude group, subgroup or single test case from executing, where
                               :               N is name of group, subgroup or case. Excluded items should be separated by comma.
                               :               Option should be used as the first argument after list of executed groups, grids, and test cases.
                               :   -parallel N: run N parallel processes (default is number of CPUs, 0 to disable)
                               :   -refresh N: save summary logs every N seconds (default 600, minimal 1, 0 to disable)
                               :   -outdir dirname: set log directory (should be empty or non-existing)
                               :   -overwrite: force writing logs in existing non-empty directory
                               :   -xml filename: write XML report for Jenkins (in JUnit-like format)
                               :   -beep: play sound signal at the end of the tests
                               :   -regress dirname: re-run only a set of tests that have been detected as regressions on some previous run.
                               :   -skipped dirname: re-run only a set of tests that have been skipped on some previous run.
                               :                     Here "dirname" is path to directory containing results of previous run.
                               :   -skip N: skip first N tests (useful to restart after abort)
                               :   Groups, grids, and test cases to be executed can be specified by list of file 
                               :   masks, separated by spaces or comma; default is all (*).
testsummarize                  :   Regenerate summary log in the test directory from logs of test cases.
                               :   This can be necessary if test grids are executed separately (e.g. on
                               :   different stations) or some grids have been re-executed.
                               :   Use: testsummarize dir
whatis                         : whatis object1 object2 ...
cprj                           : cprj result w s x y z: Conical projection of w (wire or edge) on s (faces).
prj                            : prj result w s x y z: Cylindrical projection of w (wire or edge) on s (faces) along direction.
DrawDisplay                    : DrawDisplay (DF, entry)
DrawErase                      : DrawErase (DF, entry)
DrawOwner                      : DrawOwner (drawable)
DrawRepaint                    : update the draw viewer
DrawUpdate                     : DrawUpdate (DF, entry)
PNT                            : PNT (DF, entry, x, y, z)
rmdraw                         : rmdraw(name)
DT_ApplySeq                    : DT_ApplySeq result shape rscfilename [prefix]
DT_ClosedSplit                 : result shape
DT_ShapeConvert                : DT_ShapeConvert Result Shape convert2d convert3d: Converts curves to beziers
DT_ShapeConvertRev             : DT_ShapeConvert Result Shape convert2d convert3d: Converts curves to beziers
DT_ShapeDivide                 : DT_ShapeDivide Result Shape Tol: Divides shape with C1 Criterion
DT_SplitAngle                  : DT_SplitAngle Result Shape [MaxAngle=95]: Divides revolved surfaces on segments less MaxAngle deg
DT_SplitByArea                 : result shape maxarea [preci]
DT_SplitCurve                  : DT_SplitCurve Curve Tol: Splits the curve with C1 criterion
DT_SplitCurve2d                : DT_SplitCurve2d Curve Tol: Splits the curve with C1 criterion
DT_SplitSurface                : DT_SplitSurface Result Surface/GridSurf Tol: Splits the surface with C1 criterion
DT_ToBspl                      : result shape [options=erop]
RemoveIntWires                 : result minarea wholeshape [faces or wires] [moderemoveface ]
SPApply                        : SPApply result shape rscfilename [sequence]
anaface                        : nomface
bsplres                        : BSplineRestriction result shape tol3d tol2d reqdegree reqnbsegments continuity3d continuity2d PriorDeg RationalConvert
checkedge                      : edge [face]
checkfclass2d                  : face ucoord vcoord [tol]
checkoverlapedges              : edge1 edge2 [toler domaindist]
checkselfintersection          : wire [face]
comptol                        : shape [nbpoints]
connectedges                   : res shape [toler shared]
convtorevol                    : convtorevol result shape
copytranslate                  : result shape dx dy dz
directfaces                    : directfaces result shape
edgesameparam                  : nom shape draw ou * [+ option force]
expshape                       : expshape shape maxdegree maxseg [min_continuity]
fixshape                       : res shape [preci [maxpreci]] [{switches}]
                               :   [-maxtaila <degrees>] [-maxtailw <width>]
fixsmall                       : result shape [toler=1.]
fixsmalledges                  : result shape [toler mode amxangle]
fixsmallfaces                  : result shape [toler=1.]
fixwgaps                       : result shape [toler=0]
freebounds                     : shp toler [splitclosed [splitopen]] - free bounds; toler <= 0 for shells (no sewing call)
offset2dcurve                  : result curve offset
offsetcurve                    : result curve offset dir
projcurve                      : nom_edge | curve3d | curve3d first last + X Y Z
projface                       : nom_face X Y [Z]
projpcurve                     : edge face tol x y z [start_param]
reface                         : shape result : controle sens wire
removeloc                      : result shape [remove_level(see ShapeEnum)]
reshape                        :     reshape : result shape [-replace what with] [-remove what] [-until level]
                               :     Basic utility for topological modification: 
                               :       '-replace what with'   Replaces 'what' sub-shape with 'with' sub-shape
                               :       '-remove what'         Removes 'what' sub-shape
                               :     Requests '-replace' and '-remove' can be repeated many times.
                               :     '-until level' specifies level until which shape for replcement/removal
                               :     will be searched.
scaleshape                     : scaleshape result shape scale
settolerance                   : shape [mode=v-e-f-a] val(fix value) or tolmin tolmax
sortcompound                   : shape_entree shape_result type=v-e-w-f-s-so [mode=n-e-c-x]
splitface                      : result face [u usplit1 usplit2...] [v vsplit1 vsplit2 ...]
statshape                      : shape [particul] : stats/particularites
stwire                         : stwire tout court pour help complet
tolerance                      : shape [tolmin tolmax:real]
unifysamedom                   : unifysamedom result shape [s1 s2 ...] [-f] [-e] [-nosafe] [+b] [+i] [-t val] [-a val]
fsdread                        : fsdread filename shape [name | or key 'restore_with_names']
fsdwrite                       : fsdrite shape filename [driver]
approxplate                    : approxplate result nbrpntoncurve nbrcurfront edge face tang (0:vif;1:tang) ... tol nmax degmax crit
filling                        : filling result nbB nbC nbP [SurfInit] [edge][face]order... edge[face]order... point/u v face order...
fillingparam                   : fillingparam : no arg give help
gplate                         : gplate result nbrcurfront nbrpntconst [SurfInit] [edge 0] [edge tang (1:G1;2:G2) surf]... [point] [u v tang (1:G1;2:G2) surf] ...
plate                          : plate result nbrpntoncurve nbrcurfront edge face tang (0:vif;1:tang) ...
continuity                     : continuity [tolerance] shape1 shape2 ...
encoderegularity               : encoderegularity shape [tolerance (in degree)]
fastsewing                     : fastsewing result [-tol <value>] <list_of_faces>
getedgeregularity              : getedgeregularity edge face1 [face2]
mkface                         : mkface facename surfacename [ufirst ulast vfirst vlast] [wire [norient]]
mkplane                        : mkplane facename wirename [OnlyPlane 0/1]
mkshell                        : mkshell shellname surfacename [ufirst ulast vfirst vlast] [segment 0/1]
mksurface                      : mksurface surfacename facename
pcurve                         : pcurve [name edgename] facename
projponf                       : projponf face pnt [extrema flag: -min/-max/-minmax] [extrema algo: -g(grad)/-t(tree)]
                               :         Project point on the face.
quilt                          : quilt compoundname shape1 edgeshape2  edgeshape1... shape2  edgeshape3 edgeshape1or2 ... shape3 ...
sewing                         : sewing result [tolerance] shape1 shape2 ... [min tolerance] [max tolerance] [switches]
addsweep                       : addsweep wire [vertex] [-M ] [-C] [auxiilaryshape]:no args to get help
buildsweep                     : builsweep [r] [option] [Tol] , no args to get help
deletesweep                    : deletesweep wire, To delete a section
errorsweep                     : errorsweep: returns the summary error on resulting surfaces reached by Sweep
evolved                        : evolved , no args to get help
gener                          : gener result wire1 wire2 [..wire..]
geompipe                       : geompipe r spineedge profileedge radius [byACR [byrotate]]
middlepath                     : middlepath res shape startshape endshape
mksweep                        : mksweep wire
pipe                           : pipe result Wire_spine Profile [Mode [Approx]], no args to get help
prism                          : prism result base dx dy dz [Copy | Inf | Seminf]
pruled                         : pruled result Edge1/Wire1 Edge2/Wire2
revol                          : revol result base px py pz dx dy dz angle [Copy]
setsweep                       : setsweep  no args to get help
simulsweep                     : simulsweep r [n] [option]
thrusections                   : thrusections [-N] result issolid isruled shape1 shape2 [..shape..], the option -N means no check on wires, shapes must be wires or vertices (only first or last)
clintedge                      : clintedge shape
computetolerance               : computetolerance shape
facintedge                     : facintedge shape
fuseedge                       : fuseedge shape
listfuseedge                   : listfuseedge shape
shapeG0continuity              : shapeG0continuity  shape  edge nbeval [epsnul [epsG0]]
shapeG1continuity              : shapeG1continuity  shape  edge nbeval [epsnul [epsG0 [epsG1]]]
shapeG2continuity              : shapeG2continuity shape  edge  nbeval [epsnul [epsG0 [epsG1 [maxlen [perce]]]]]
tolsphere                      : toolsphere shape
                               :         shows vertex tolerances by drawing spheres
validrange                     : validrange edge [(out) u1 u2]
                               :         computes valid range of the edge, and
                               :         prints first and last values or sets the variables u1 and u2
addpcurve                      : addpcurve edge 2dcurve face [tol (default 1.e-7)]
bmirror                        : bmirror name x y z dx dy dz
bmove                          : bmove name1 name2 ... name, set location from name
bounding                       : bounding {shape | xmin ymin zmin xmax ymax zmax}
                               :            [-obb] [-noTriangulation] [-optimal] [-extToler]
                               :            [-dump] [-print] [-dumpJson] [-shape name] [-nodraw] [-finitePart]
                               :            [-save xmin ymin zmin xmax ymax zmax]
                               :
                               : Computes a bounding box. Two types of the source data are supported:
                               : a shape or AABB corners (xmin, ymin, zmin, xmax, ymax, zmax).
                               :
                               : Calculation options (applicable only if input is a shape):
                               :  -obb     Compute Oriented Bounding Box (OBB) instead of AABB.
                               :  -noTriangulation Force use of exact geometry for calculation
                               :                   even if triangulation is present.
                               :  -optimal Force calculation of optimal (more tight) AABB.
                               :           In case of OBB:
                               :           - for PCA approach applies to initial AABB used in OBB calculation
                               :           - for DiTo approach modifies the DiTo algorithm to check more axes.
                               :  -extToler Include tolerance of the shape in the resulting box.
                               :
                               : Output options:
                               :  -dump    Prints the information about computed Bounding Box.
                               :  -print   Prints the information about computed Bounding Box.
                               :           It is enabled by default (with plain old syntax for AABB)
                               :           if neither -shape nor -save is specified.
                               :  -dumpJson Prints DumpJson information about Bounding Box.
                               :  -shape   Stores computed box as solid in DRAW variable with specified name.
                               :  -save    Stores min and max coordinates of AABB in specified variables.
                               :  -noDraw  Avoid drawing resulting Bounding Box in DRAW viewer.
                               :  -finite  Return finite part of infinite box.
brotate                        : brotate name1 name2 ... x y z dx dy dz angle
bscale                         : bscale name x y z scale
btranslate                     : btranslate name1 name2 ... dx dy dz
checkloc                       : checkloc shape 
compare                        : Compare shapes. Usage: compare shape1 shape2
deform                         : deform newname name CoeffX CoeffY CoeffZ
findplane                      : findplane name planename 
fmirror                        : fmirror name x y z dx dy dz
fmove                          : fmove name1 name2 ... name, set location from name
fsameparameter                 : fsameparameter shapename [tol (default 1.e-7)], 
                               : force sameparameter on all edges of the shape
fscale                         : fscale name x y z scale
gbounding                      : gbounding surf/curve/curve2d [-o] 
getcoords                      : getcoords vertex1 vertex 2... ; shows coords of input vertices
isbbinterf                     : isbbinterf shape1 shape2 [-o]
                               : Checks whether the bounding-boxes created from the given shapes are interfered. If "-o"-option is switched on then the oriented boxes will be checked. Otherwise, axes-aligned boxes will be checked.
issubshape                     : issubshape subshape shape
                               :         Check if the shape is sub-shape of other shape and get its index in the shape.
maxtolerance                   : maxtolerance shape 
mkedgecurve                    : mkedgecurve name tolerance
nproject                       : nproject pj e1 e2 e3 ... surf -g -d [dmax] [Tol [continuity [maxdeg [maxseg]]]
nurbsconvert                   : nurbsconvert result name [result name]
precision                      : precision [preci]
purgeloc                       : purgeloc res shape 
reperageshape                  : reperage shape -> list of shape (result of interstion shape , line)
reset                          : reset name1 name2 ..., remove location
sameparameter                  : sameparameter [result] shape [tol]
scalexyz                       : scalexyz res shape factor_x factor_y factor_z
solidorientation               : orientsolid myClosedSolid
tcopy                          : tcopy [-n(ogeom)] [-m(esh)] name1 result1 [name2 result2 ...]
tmirror                        : tmirror name x y z dx dy dz [-copy]
tmove                          : tmove name1 name2 ... name, set location from name [-copy]
trotate                        : trotate name1 name2 ... x y z dx dy dz angle [-copy]
tscale                         : tscale name x y z scale [-copy]
ttranslate                     : ttranslate name1 name2 ... dx dy dz [-copy]
updatetolerance                : updatetolerance [result] shape [param] 
                               :   if [param] is absent - not verify of face tolerance, else - perform it
vecdc                          : vecdc + Pointe double click 
wexplo                         : wexplo wire [face] create WEDGE_i
checkdiff                      : checks the validity of the diff between the shapes arg1..argn and result :
                               :  checkdiff arg1 [arg2..argn] result [closedSolid (1/0)] [geomCtrl (1/0)]
checksection                   : checks the closure of a section : checksection name [-r <RefVal>]
                               : "-r" - allowed number of alone vertices.
checkshape                     : checkshape : no args to have help
2dprofile                      : 2dprofile, no args to get help
bsplineprof                    : bsplineprof, no args to get help
build3d                        : build3d S [tol]
concatC0wire                   : concatC0wire result wire
concatwire                     : concatwire result wire [option](G1/C1)
edge                           : edge edgename v1 v2
edgeintersector                : edgeintersector r E1 E2 F [Tol]
etrim                          : etrim edge v1 [v2]
mk2dcurve                      : mk2dcurve curve edge [face OR index]
mkcurve                        : mkcurve curve edge
mkedge                         : mkedge edge curve [surface] [pfirst plast] [vfirst [pfirst] vlast [plast]] 
mkoffset                       : mkoffset result face/compound of wires  nboffset stepoffset [jointype(a/i) [alt]]
mkoricurve                     : mkoricurve curve edge: 
                               :   the curve is colored according to the orientation of the edge
mkpoint                        : mkpoint point vertex
openoffset                     : openoffset result face/wire nboffset stepoffset [jointype(a/i)]
pickface                       : pickface
polyline                       : polyline name x1 y1 z1 x2 y2 z2 ...
polyvertex                     : polyvertex name v1 v2 ...
profile                        : profile, no args to get help
range                          : range edge [face] first last
reducepcurves                  : reducepcurves shape1 shape2 ...
transfert                      : transfert edge1 edge2
uisoedge                       : uisoedge edge face u v1 v2
vertex                         : vertex name [x y z | p edge | poin]
visoedge                       : visoedge edge face v u1 u2
wire                           : wire wirename [-unsorted] e1/w1 [e2/w2 ...]
dist                           : dist Shape1 Shape2
distmini                       : distmini name Shape1 Shape2 [deflection] [-parallel]
proximity                      : proximity Shape1 Shape2 [-tol <value>] [-profile]
                               : Searches for pairs of overlapping faces of the given shapes.
                               : The options are:
                               :   -tol     : non-negative tolerance value used for overlapping
                               :              test (for zero tolerance, the strict intersection
                               :              test will be performed)
                               :   -profile : outputs execution time for main algorithm stages
selfintersect                  : selfintersect Shape [-tol <value>] [-profile]
                               : Searches for intersected/overlapped faces in the given shape.
                               : The algorithm uses shape tessellation (should be computed in
                               : advance), and provides approximate results. The options are:
                               :   -tol     : non-negative tolerance value used for overlapping
                               :              test (for zero tolerance, the strict intersection
                               :              test will be performed)
                               :   -profile : outputs execution time for main algorithm stages
addslide                       :  Adds sliding elements : addslide prism/revol/pipe edge face [edge face...]
blindhole                      :  Performs the blind hole : blindhole result shape Or.X Or.Y Or.Z Dir.X Dir.Y Dir.Z Radius Length
bossage                        :  Perform fillet on top and bottom edges of dprism :bossage dprism result radtop radbottom First/LastShape (1/2)
endedges                       :  Return top and bottom edges of dprism :endedges dprism shapetop shapebottom First/LastShape (1/2)
featdprism                     : Defines the arguments for a drafted prism : featdprism shape face skface angle Fuse(0/1/2) Modify(0/1)
featlf                         : Defines the arguments for a linear rib or slot : featlf shape wire plane DirX DirY DirZ DirX DirY DirZ Fuse(0/1/2) Modify(0/1)
featperform                    :  Performs the prism revol dprism linform or pipe :featperform prism/revol/pipe/dprism/lf result [[Ffrom] Funtil]
featperformval                 :  Performs the prism revol dprism or linform with a value :featperformval prism/revol/dprism/lf result value
featpipe                       : Defines the arguments for a pipe : featpipe shape element skface  spine Fuse(0/1/2) Modify(0/1)
featprism                      : Defines the arguments for a prism : featprism shape element skface  Dirx Diry Dirz Fuse(0/1/2) Modify(0/1)
featrevol                      : Defines the arguments for a revol : featrevol shape element skface  Ox Oy Oz Dx Dy Dz Fuse(0/1/2) Modify(0/1)
featrf                         : Defines the arguments for a rib or slot of revolution : featrf shape wire plane X Y Z DirX DirY DirZ Size Size Fuse(0/1/2) Modify(0/1)
fillet                         :  Perform fillet on compounds of edges :fillet result object rad1 comp1 rad2 comp2 ...
firsthole                      :  Performs the first hole : firsthole result shape Or.X Or.Y Or.Z Dir.X Dir.Y Dir.Z Radius
fprism                         : Prisms a set of faces of a shape : fprism f[use]/c[ut] result shape [[FaceFrom] FaceUntil] VecX VecY VecZ face1 [face2...]
frotate                        : Rotates a set of faces of a shape : frotate f[use]/c[ut] result shape Angle/[FaceFrom] FaceUntil OX OY OZ DX DY DZ face1 [face2...]
glue                           : glue result shapenew shapebase facenew facebase [facenew facebase...] [edgenew edgebase [edgenew edgebase...]]
hole                           :  Performs a hole : hole result shape Or.X Or.Y Or.Z Dir.X Dir.Y Dir.Z Radius [Pfrom Pto]
holecontrol                    : Sets/Unsets or display controls on holes : holecontrol [0/1]
holend                         :  Performs the hole til end : holend result shape Or.X Or.Y Or.Z Dir.X Dir.Y Dir.Z Radius
localope                       :  Performs a local top. operation : localope result shape tool F/C (fuse/cut) face [face...]
offsetcompshape                : offsetcompshape r shape offset [face ...]
offsetload                     : offsetload shape offset bouchon1 bouchon2 ...
offsetonface                   : offsetonface face1 offset1 face2 offset2 ...
offsetparameter                : offsetparameter Tol Inter(c/p) JoinType(a/i/t) [RemoveInternalEdges(r/k)]
offsetperform                  : offsetperform result
offsetshape                    : offsetshape r shape offset [tol] [face ...]
offsetshapesimple              : offsetshapesimple result shape offsetvalue [solid] [tolerance=1e-7]
splitshape                     : splitshape result shape [splitedges] [face wire/edge/compound [wire/edge/compound ...][face wire/edge/compound [wire/edge/compound...] ...] [@ edgeonshape edgeonwire [edgeonshape edgeonwire...]]
thickshell                     : thickshell r shape offset [jointype [tol] ]
wprism                         : Prisms wires on a face : wprism f[use]/c[ut] result shape [[FaceFrom] FaceUntil] VecX VecY VecZ  SkecthFace wire1 [wire2 ....]
wrotate                        : Rotates wires on a face : wrotate f[use]/c[ut] result shape Angle/[FFrom] FUntil OX OY OZ DX DY DZ SkecthFace wire1 [wire2 ....]
bcutblend                      : bcutblend result shape1 tool radius [-d]
bfuseblend                     : bfuseblend result shape1 shape2 radius [-d]
blend                          : blend result object rad1 ed1 rad2 ed2 ... [R/Q/P]
blend1                         : blend1 result object rad ed1  ed2 ...
brollingball                   : brollingball r S radius [stopf1 ..] @ [f1 f2 ..] @ [e1 ..]
buildevol                      : buildevol end of the evol fillet computation
chamf                          : for help call chamf without arguments
chamf_throat                   : chamf_throat result shape edge throat
chamf_throat_with_penetration  : chamf_throat_with_penetration result shape edge face offset throat
checkhist                      : checkhist
continuityblend                : continuityblend C0/C1/C2  [tangle]
mkevol                         : mkevol result object (then use updatevol) [R/Q/P]
rollingball                    : rollingball  r S radius [stopf1 ..] @ [f1 f2 ..] @ [e1 ..]
tolblend                       : tolblend [ta t3d t2d fl]
trollingball                   : trollingball r S radius [stopf1 ..] @ [f1 f2 ..] @ [e1 ..]
updatevol                      : updatevol edge u1 rad1 u2 rad2 ...
chamfer2d                      : chamfer2d result wire (or edge1 edge2) length1 length2
chfi2d                         : chfi2d result face [edge1 edge2 (F radius/CDD d1 d2/CDA d ang) ....]
fillet2d                       : fillet2d result wire (or edge1 edge2) radius
buildfaces                     : buildfaces result faceReference wire1 wire2 ...
halfspace                      : halfspace result face/shell x y z
BRepIntCS                      : Calcul d'intersection entre face et curve : BRepIntCS curve1 [curve2 ...] shape [res] [tol]
makeboss                       : create a boss on the shape myS
mksh                           : create a shell on Shape
shape                          : shape name V/E/W/F/Sh/So/CS/C; make a empty shape
subshape                       : subshape name V/E/W/F/Sh/So/CS/C index; get subsshape <index> of given type
xbounds                        : xbounds face
xclassify                      : use xclassify Solid [Tolerance=1.e-7]
xdistc2dc2dss                  : xdistc2dc2dss c2d_1 c2d_2 s1 s2 t1 t2 nbp
xdistcc                        : xdistcc c1 c2 t1 t2 nbp
xdistcc2ds                     : xdistcc2ds c c2d s t1 t2 nbp
xdistcs                        : xdistcs curve surface t1 t2 nbpoints [tol [warn_tol]]
GetUTF                         : GetUTF (DF, entry, fileName)
SetUTFName                     : SetUTFName (DF, entry, fileName)
appro                          : appro result nbpoint [curve]
drawcont                       : display current contour
extrema                        : extrema curve/surface curve/surface [extended_output = 0|1]
grilapp                        : grilapp result nbupoint nbvpoint X0 dX Y0 dY z11 z12 .. z1nu ....  
mat                            : computes the mat: mat [a/i [o]]
proj                           : proj curve/surf x y z [{extrema algo: g(grad)/t(tree)}|{u v}]
                               :         Optional parameters are relevant to surf only.
                               :         If initial {u v} are given then local extrema is called
result                         : result
side                           : side left/right
surfapp                        : surfapp result nbupoint nbvpoint x y z ....
surfint                        : surfint result surf nbupoint nbvpoint [uperiodic]
topoload                       : load face
totalextcc                     : totalextcc curve curve
zone                           : zone edge or vertex
2dbarycen                      : 2dbarycen x1 y1 x2 y2 par
                               :   returns 2D point of a given parameter between two points 
2dcross                        : 2dcross x1 y1 x2 y2
                               :   returns cross product of two 2D vectors 
2ddistlp                       : 2ddistlp xo yo dx dy xp yp
                               :   returns distance between 2D line and point 
2ddistpp                       : 2ddistpp x1 y1 x2 y2
                               :   returns distance between two 2D points 
2ddistppp                      : 2ddistppp x1 y1 x2 y2 x3 y3
                               :   returns deviation of 2D point p2 from segment p1-p3 (sign shows the side) 
2ddot                          : 2ddot x1 y1 x2 y2
                               :   returns scalar product of two 2D vectors 
2ddrseg                        : 2ddrseg name x1 y1 x2 y2
                               :   creates a trimmed 2D line between two 2D points 
2dinverse                      : 2dinverse x y
                               :   returns inversed 2D vector 
2dmodule                       : 2dmodule x y
                               :   returns module of a 2D vector 
2dnorm                         : 2dnorm x y
                               :   returns unified vector from a given 2D vector 
2dort                          : 2dort x y
                               :   returns 2D vector rotated on 90 degrees 
2dpntc                         : 2dpntc curv2d u
                               :   returns coordinates of 2D point on 2D curve with given parameter 
2dscale                        : 2dscale x y factor
                               :   returns 2D vector multiplied by scalar 
2dvec                          : 2dvec x1 y1 x2 y2
                               :   returns coordinates of 2D vector between two 2D points 
2dvecangle                     : 2dvecangle x1 y1 x2 y2
                               :   returns angle between two vectors 
barycen                        : barycen x1 y1 z1 x2 y2 z2 par
                               :   returns point of a given parameter between two points 
cross                          : cross x1 y1 z1 x2 y2 z2
                               :   returns cross product of two vectors 
distlp                         : distlp xo yo zo dx dy dz xp yp zp
                               :   returns distance between line and point 
distplp                        : distplp xo yo zo dx dy dz xp yp zp
                               :   returns distance between plane and point 
distpp                         : distpp x1 y1 z1 x2 y2 z2
                               :   returns distance between two points 
distppp                        : distppp x1 y1 z1 x2 y2 z2 x3 y3 z3
                               :   returns deviation of point p2 from segment p1-p3 
dot                            : dot x1 y1 z1 x2 y2 z2
                               :   returns scalar product of two vectors 
drseg                          : drseg name x1 y1 z1 x2 y2 z2
                               :   creates a trimmed line between two points 
inverse                        : inverse x y z
                               :   returns inversed vector 
mdist                          : compute distance between two points of mouse clicks 
module                         : module x y z
                               :   returns module of a vector 
mpick                          : show coordinates at mouse click 
norm                           : norm x y z
                               :   returns unified vector from a given vector 
pln                            : pln x1 y1 z1 x2 y2 z2 x3 y3 z3
                               :   returns plane built on three points 
pnt                            : pnt point_or_vertex
                               :   returns coordinates of point in the given Draw variable of type point or vertex 
pntc                           : pntc curve u
                               :   returns coordinates of point on curve with given parameter 
pntcons                        : pntcons curv2d surf u
                               :   returns coordinates of point on surface defined by 
                               :   point on 2D curve with given parameter 
pntsu                          : pntsu surf u v
                               :   returns coordinates of point on surface with given parameters 
scale                          : scale x y z factor
                               :   returns vector multiplied by scalar 
vec                            : vec x1 y1 z1 x2 y2 z2
                               :   returns coordinates of vector between two points 
vecangle                       : vecangle x1 y1 z1 x2 y2 z2
                               :   returns angle between two vectors 
vblend                         : vblend result object rad1 ed1 rad2 ed2 ... [R/Q/P]
XAddDatum                      : XAddDatum Doc shape1/label1 ... shapeN/labelN
XAddDatumModifier              : XAddDatumModifier Doc Datum_Label mod1 mod2 ...
                               : Values:
                               :   0 AnyCrossSection
                               :   1 Any_LongitudinalSection
                               :   2 Basic
                               :   3 ContactingFeature
                               :   4 DegreeOfFreedomConstraintU
                               :   5 DegreeOfFreedomConstraintV
                               :   6 DegreeOfFreedomConstraintW
                               :   7 DegreeOfFreedomConstraintX
                               :   8 DegreeOfFreedomConstraintY
                               :   9 DegreeOfFreedomConstraintZ
                               :  10 DistanceVariable
                               :  11 FreeState
                               :  12 LeastMaterialRequirement
                               :  13 Line
                               :  14 MajorDiameter
                               :  15 MaximumMaterialRequirement
                               :  16 MinorDiameter
                               :  17 Orientation
                               :  18 PitchDiameter
                               :  19 Plane
                               :  20 Point
                               :  21 Translation
XAddDimension                  : XAddDimension Doc shape/label [shape/label]
XAddDimensionDescr             : XAddDimensionDescr Doc Dim_Label Description [DescriptionName]
                               : Add named text description to given Dimension, if DescriptionName is missedname will be an empty string.
XAddDimensionModifiers         : XAddDimensionModifiers Doc Dim_Label mod1 mod2 ...Values:     0 ControlledRadius
                               :      1 Square
                               :      2 StatisticalTolerance
                               :      3 ContinuousFeature
                               :      4 TwoPointSize
                               :      5 LocalSizeDefinedBySphere
                               :      6 LeastSquaresAssociationCriterion
                               :      7 MaximumInscribedAssociation
                               :      8 MinimumCircumscribedAssociation
                               :      9 CircumferenceDiameter
                               :     10 AreaDiameter
                               :     11 VolumeDiameter
                               :     12 MaximumSize
                               :     13 MinimumSize
                               :     14 AverageSize
                               :     15 MedianSize
                               :     16 MidRangeSize
                               :     17 RangeOfSizes
                               :     18 AnyRestrictedPortionOfFeature
                               :     19 AnyCrossSection
                               :     20 SpecificFixedCrossSection
                               :     21 CommonTolerance
                               :     22 FreeStateCondition
                               :     23 Between
XAddGeomTolerance              : XAddGeomTolerance Doc shape/label
XAddTolModifier                : XAddTolModifier Doc Tol_Label mod1 mod2 ...Values:
                               :       0 Any_Cross_Section
                               :       1 Common_Zone
                               :       2 Each_Radial_Element
                               :       3 Free_State
                               :       4 Least_Material_Requirement
                               :       5 Line_Element
                               :       6 Major_Diameter
                               :       7 Maximum_Material_Requirement
                               :       8 Minor_Diameter
                               :       9 Not_Convex
                               :      10 Pitch_Diameter
                               :      11 Reciprocity_Requirement
                               :      12 Separate_Requirement
                               :      13 Statistical_Tolerance
                               :      14 Tangent_Plane
XDumpDGTs                      : XDumpDGTs Doc shape/label/all 
XDumpNbDGTs                    : XDumpNbDGTs Doc [f (full dumping)]
XGetDatum                      : XGetDatum Doc GeomTol_Label/Shape_Label
XGetDatumModifiers             : XGetDatumModifiers Doc Datum_Label
XGetDatumName                  : XGetDatumName Doc Datum_Label
XGetDatumPosition              : XGetDatumPosition Doc Datum_Label
XGetDimensionClassOfTol        : XGetDimensionClassOfTol Doc Dim_Label
XGetDimensionDescr             : XGetDimensionDescr Doc Dim_Label
                               : Return all descriptions of given Dimension.
XGetDimensionDir               : XGetDimensionDir Doc Dim_Label
XGetDimensionModifiers         : XGetDimensionModifiers Doc Dim_Label
XGetDimensionNbOfDecimalPlaces : XGetDimensionNbOfDecimalPlaces Doc Dim_Label
XGetDimensionPlusMinusTol      : XGetDimensionPlusMinusTol Doc Dim_Label
XGetDimensionPoints            : XGetDimensionPoints Doc Dim_Label
XGetDimensionQualifier         : XGetDimensionQualifier Doc Dim_Label
XGetDimensionRange             : XGetDimensionRange Doc Dim_Label
XGetDimensionType              : XGetDimensionType Doc Dim_Label
XGetDimensionValue             : XGetDimensionValue Doc Dim_Label
XGetGDTAffectedPlane           : XGetGDTAffectedPlane Doc GDT_Label PlaneReturns affected plane into Plane
XGetGDTPosition                : XGetGDTPosition Doc GDT_LabelReturns text position and plane, parallel to which dimension is displayed
XGetGDTPresentation            : XGetGDTPresentation Doc GDT_Label ShapeReturns Presentation into Shape
XGetGDTSemanticName            : XGetGDTSemanticName Doc GDT_Label
XGetTolMaterialReq             : XGetTolMaterialReq Doc GTol_Label
XGetTolMaxValue                : XGetTolMaxValue Doc Dim_Label val
XGetTolModifier                : XGetTolModifier Doc Tol_Label
XGetTolZoneMod                 : XGetTolZoneMod Doc GTol_Label
XGetTolZoneModValue            : XGetTolZoneModValue Doc GTol_Label
XGetToleranceValue             : XGetToleranceValue Doc GTol_Label
XGetTypeOfTolerance            : XGetTypeOfTolerance Doc GTol_Label
XGetTypeOfToleranceValue       : XGetTypeOfToleranceValue Doc GTol_Label
XSetDatum                      : XSetDatum Doc Datum_Label GeomTol_Label
XSetDatumName                  : XSetDatumName Doc Datum_Label name
XSetDatumPosition              : XSetDatumPosition Doc Datum_Label position[1-3]Set datum position number in geometric tolerance datum system
XSetDimensionClassOfTol        : XSetDimensionClassOfTol Doc Dim_Label ishole[1/0] formVar gradeValues of formVar:     1 a
                               :      2 b
                               :      3 c
                               :      4 cd
                               :      5 d
                               :      6 e
                               :      7 ef
                               :      8 f
                               :      9 fg
                               :     10 g
                               :     11 h
                               :     12 js
                               :     13 j
                               :     14 k
                               :     15 m
                               :     16 n
                               :     17 p
                               :     18 r
                               :     19 s
                               :     20 t
                               :     21 u
                               :     22 v
                               :     23 x
                               :     24 y
                               :     25 z
                               :     26 za
                               :     27 zb
                               :     28 zc
                               : 
                               : Values of grade:     0 01
                               :      1 0
                               :      2 1
                               :      3 2d
                               :      4 3
                               :      5 4
                               :      6 5f
                               :      7 76
                               :      8 7g
                               :      9 8
                               :     10 9
                               :     11 10js
                               :     12 11j
                               :     13 12k
                               :     14 13m
                               :     15 14n
                               :     16 15p
                               :     17 16r
                               :     18 17s
                               :     19 18t
XSetDimensionDir               : XSetDimensionDir Doc Dim_Label x y z
XSetDimensionNbOfDecimalPlaces : XSetDimensionNbOfDecimalPlaces Doc Dim_Label l_val r_val
XSetDimensionPath              : XSetDimensionPath Doc Dim_Label path(edge)
XSetDimensionPlusMinusTol      : XSetDimensionPlusMinusTol Doc Dim_Label low_val up_val
XSetDimensionPoints            : XSetDimensionPoints Doc Dim_Label v1 [v2]
XSetDimensionQualifier         : XSetDimensionQualifier Doc Dim_Label valValues:
                               :   0 none
                               :   1 Min
                               :   2 Max
                               :   3 Avg
XSetDimensionRange             : XSetDimensionRange Doc Dim_Label low_val up_val
XSetDimensionType              : XSetDimensionType Doc Dim_Label typeValues:      0 type is absent
                               :       1 Location_CurvedDistance
                               :       2 Location_LinearDistance
                               :       3 Location_LinearDistance_FromCenterToOuter
                               :       4 Location_LinearDistance_FromCenterToInner
                               :       5 Location_LinearDistance_FromOuterToCenter
                               :       6 Location_LinearDistance_FromOuterToOuter
                               :       7 Location_LinearDistance_FromOuterToInner
                               :       8 Location_LinearDistance_FromInnerToCenter
                               :       9 Location_LinearDistance_FromInnerToOuter
                               :      10 Location_LinearDistance_FromInnerToInner
                               :      11 Location_Angular
                               :      12 Location_Oriented
                               :      13 Location_WithPath
                               :      14 Size_CurveLength
                               :      15 Size_Diameter
                               :      16 Size_SphericalDiameter
                               :      17 Size_Radius
                               :      18 Size_SphericalRadius
                               :      19 Size_ToroidalMinorDiameter
                               :      20 Size_ToroidalMajorDiameter
                               :      21 Size_ToroidalMinorRadius
                               :      22 Size_ToroidalMajorRadius
                               :      23 Size_ToroidalHighMajorDiameter
                               :      24 Size_ToroidalLowMajorDiameter
                               :      25 Size_ToroidalHighMajorRadius
                               :      26 Size_ToroidalLowMajorRadius
                               :      27 Size_Thickness
                               :      28 Size_Angular
                               :      29 Size_WithPath
XSetDimensionValue             : XSetDimensionValue Doc Dim_Label val
XSetGDTAffectedPlane           : XSetGDTAffectedPlane Doc GDT_Label Plane type[1 - intersection/ 2 - orientation]Set affectedP plane for geometric tolerance
XSetGDTPosition                : XSetGDTPosition Doc GDT_Label loc_x loc_y loc_z normal_x normal_y normal_z xdir_x xdir_y xdir_zSet plane to display dimension parallel to and point to display text (loc)
XSetGDTPresentation            : XSetGDTPresentation Doc GDT_Label Shape NameSet presentation with given name for dimension
XSetGDTSemanticName            : XSetGDTSemanticName Doc GDT_Label NameSet semantic name
XSetTolMaterialReq             : XSetTolMaterialReq Doc GTol_Label modValues:
                               :   0 none
                               :   1 M
                               :   2 L
XSetTolMaxValue                : XSetTolMaxValue Doc Dim_Label val
XSetTolZoneMod                 : XSetTolZoneMod Doc GTol_Label modValues:
                               :   0 none
                               :   1 P
                               :   2 NonUniform
XSetTolZoneModValue            : XSetTolZoneModValue Doc GTol_Label val
XSetToleranceValue             : XSetToleranceValue Doc GTol_Label value
XSetTypeOfTolerance            : XSetTypeOfTolerance Doc GTol_Label typeValues:
                               :       0 type is absent
                               :       1 Angularity
                               :       2 CircularRunout
                               :       3 CircularityOrRoundness
                               :       4 Coaxiality
                               :       5 Concentricity
                               :       6 Cylindricity
                               :       7 Flatness
                               :       8 Parallelism
                               :       9 Perpendicularity
                               :      10 Position
                               :      11 ProfileOfLine
                               :      12 ProfileOfSurface
                               :      13 Straightness
                               :      14 Symmetry
                               :      15 TotalRunout
XSetTypeOfToleranceValue       : XSetTypeOfToleranceValue Doc GTol_Label typeValues:
                               :   0 none
                               :   1 Diameter
                               :   2 SphericalDiameter
XNoteAdd                       : XNoteAdd Doc note item [--attr guid | --subshape num]
XNoteAnnotations               : XNoteAnnotations Doc
XNoteCount                     : XNoteCount Doc
XNoteCreateBalloon             : XNoteCreateBalloon Doc comment [--user name] [--time stamp]
XNoteCreateBinData             : XNoteCreateBinData Doc title <--file path | --data data> [--mime type] [--user name] [--time stamp]
XNoteCreateComment             : XNoteCreateComment Doc comment [--user name] [--time stamp]
XNoteDelete                    : XNoteDelete Doc note
XNoteDeleteAll                 : XNoteDeleteAll Doc
XNoteDeleteOrphan              : XNoteDeleteOrphan Doc
XNoteDump                      : XNoteDump Doc note
XNoteFindAnnotated             : XNoteFindAnnotated Doc item [--attr guid | --subshape num]
XNoteGetNotes                  : XNoteGetNotes Doc item [--attr guid | --subshape num]
XNoteIsRefOrphan               : XNoteIsRefOrphan Doc ref
XNoteNotes                     : XNoteNotes Doc
XNoteRefDump                   : XNoteRefDump Doc ref
XNoteRemove                    : XNoteRemove Doc item note [--attr guid | --subshape num] [--del-orphan]
XNoteRemoveAll                 : XNoteRemoveAll Doc item [--attr guid] [--subshape num] [--del-orphan]
XNoteTimestamp                 : XNoteTimestamp Doc note
XNoteUsername                  : XNoteUsername Doc note
XAddClippingPlane              : XAddClippingPlane Doc plane name capping[0/1]
XDumpView                      : XDumpView Doc ViewLabel
XGetClippingPlane              : XGetClippingPlane Doc ClippingPlane_Label
XGetClippingPlaneCapping       : XGetClippingPlaneCapping Doc ClippingPlane_Label
XGetViewBackPlaneDistance      : XGetViewBackPlaneDistance Doc ViewLabel
XGetViewClippingPlanes         : XGetViewClippingPlanes Doc ViewLabelReturn labels of reference Clipping Planes
XGetViewDir                    : XGetViewDir Doc ViewLabel
XGetViewFrontPlaneDistance     : XGetViewFrontPlaneDistance Doc ViewLabel
XGetViewGDTs                   : XGetViewGDTs Doc ViewLabelReturn labels of reference GDTs
XGetViewName                   : XGetViewName Doc ViewLabel
XGetViewProjectionPoint        : XGetViewProjectionPoint Doc ViewLabel
XGetViewShapes                 : XGetViewShapes Doc ViewLabelReturn labels of reference shapes
XGetViewType                   : XGetViewType Doc ViewLabel
XGetViewUpDir                  : XGetViewUpDir Doc ViewLabel
XGetViewVolumeSidesClipping    : XGetViewVolumeSidesClipping Doc ViewLabel
XGetViewWindowSize             : XGetViewWindowSize Doc ViewLabel
XGetViewZoom                   : XGetViewZoom Doc ViewLabel
XIsView                        : XIsView Doc Label
XRemoveClippingPlane           : XRemoveClippingPlane Doc ClippingPlane_Label
XRemoveView                    : XRemoveView Doc ViewLabel
XSetClippingPlanes             : XSetView Doc view_plane plane_label1 ... plane_labelN
XSetView                       : XSetView Doc shape_label1 ... shape_labelN gdt_label1 ... gdt_labelN
XSetViewBackPlaneDistance      : XSetViewBackPlaneDistance Doc ViewLabel distance
XSetViewDir                    : XSetViewDir Doc ViewLabel x y z
XSetViewFrontPlaneDistance     : XSetViewFrontPlaneDistance Doc ViewLabel distance
XSetViewName                   : XSetViewName Doc ViewLabel name
XSetViewProjectionPoint        : XSetViewProjectionPoint Doc ViewLabel x y z
XSetViewType                   : XSetViewType Doc ViewLabel type (central/parallel/no_camera)
XSetViewUpDir                  : XSetViewUpDir Doc ViewLabel x y z
XSetViewVolumeSidesClipping    : XSetViewVolumeSidesClipping Doc ViewLabel value(0 - unset, 1- set)
XSetViewWindowSize             : XSetViewWindowSize Doc ViewLabel width height
XSetViewZoom                   : XSetViewZoom Doc ViewLabel zoom_factor
XUnsetViewBackPlaneDistance    : XUnsetViewBackPlaneDistance Doc ViewLabel
XUnsetViewFrontPlaneDistance   : XSetViewFrontPlaneDistance Doc ViewLabel
XAddColor                      : Doc R G B [alpha]    : Add color in document to color table
XAddVisMaterial                : Doc Material
                               : [-transparency 0..1] [-alphaMode {Opaque|Mask|Blend|BlendAuto} CutOffValue] [-refractionIndex 1..3]
                               : [-diffuse   RGB] [-diffuseTexture ImagePath]
                               : [-specular  RGB] [-ambient RGB] [-emissive  RGB] [-shininess 0..1]
                               : [-baseColor RGB] [-baseColorTexture ImagePath]
                               : [-emissiveFactor RGB] [-emissiveTexture ImagePath]
                               : [-metallic 0..1] [-roughness 0..1] [-metallicRoughnessTexture ImagePath]
                               : [-occlusionTexture ImagePath] [-normalTexture ImagePath]
                               : [-faceCulling {auto|backCulled|doubleSided}] [-doubleSided {0|1}]
                               : Add material into Document's material table.
XFindColor                     : Doc R G B [alpha]    : Find label where indicated color is situated
XGetAllColors                  : Doc    : Print all colors that defined in document
XGetAllVisMaterials            : Doc [{-names|-labels}=-names]    : Print all visualization materials defined in document
XGetColor                      : Doc label    : Return color defined on label in colortable
XGetInstanceColor              : Doc Shape [{generic|surface|curve}=gen]    : Return the color of component shape
XGetInstanceVisible            : Doc Shape     : Return the visibility of shape 
XGetObjVisibility              : Doc {Label|Shape}     : Return the visibility of shape 
XGetShapeColor                 : Doc Label {generic|surface|curve}    : Returns color defined by label
XGetVisMaterial                : Doc {Material|Shape}    : Print visualization material properties
XRemoveColor                   : Doc Label    : Remove color in document from color table
XRemoveVisMaterial             : Doc Material    : Remove material in document from material table
XSetColor                      : Doc {Label|Shape} R G B [alpha] [{generic|surface|curve}=gen]    : Set color [R G B] to shape given by Label, type of color 's' - for surface, 'c' - for curve (default generic)
XSetInstanceColor              : Doc Shape R G B [alpha] [{generic|surface|curve}=gen]    : sets color for component of shape if SHUO structure exists already
XSetObjVisibility              : Doc {Label|Shape} (0)     : Set the visibility of shape  
XSetVisMaterial                : Doc Shape Material    : Set material to shape
XUnsetColor                    : Doc {Label|Shape} {generic|surface|curve}    : Unset color
XUnsetVisMaterial              : Doc Shape    : Unset material from shape
XAttributeValue                : Doc label #attribute: internal command for browser
XDisplay                       : XDisplay Doc [label1 [label2 [...]]] [-explore {on|off}] [-docPrefix {on|off}] [-names {on|off}]
                               :      [-noupdate] [-dispMode Mode] [-highMode Mode] [-autoTriangulation {0|1}]
                               : Displays document (parts) in 3D Viewer.
                               :  -dispMode    Presentation display mode.
                               :  -highMode    Presentation highlight mode.
                               :  -docPrefix   Prepend document name to object names; TRUE by default.
                               :  -names       Use object names instead of label tag; TRUE by default.
                               :  -explore     Explode labels to leaves; FALSE by default.
                               :  -outDispList Set the TCL variable to the list of displayed object names.
                               :               (instead of printing them to draw interpreter)
                               :  -autoTriang  Enable/disable auto-triangulation for displayed shapes.
XGetLengthUnit                 : Doc [-scale]    : Print name of length unit
                               : -scale : print value of the scaling factor to meter of length unit
XGetViewNameMode               :     : Print if  mode of displaying names is turn on.
XNewDoc                        : DocName     : Create new DECAF document
XOpen                          : Path Doc [-skipAttribute] [-readAttribute] [-readPath] [-append|-overwrite]    : Open XDE Document with name Doc from Path
                               :          The options are:
                               :            -skipAttribute : class name of the attribute to skip during open, for example -skipTDF_Reference
                               :            -readAttribute : class name of the attribute to read only during open, for example -readTDataStd_Name loads only such attributes
                               :            -append : to read file into already existing document once again, append new attributes and don't touch existing
                               :            -overwrite : to read file into already existing document once again, overwriting existing attributes
XSave                          : [Doc Path]     : Save Doc or first document in session
XSetLengthUnit                 : Doc {unit_name|scale_factor}    : Set value of length unit
                               : Possible unit_name: m, mm, km, cm, micron, mille, in(inch), min(microinch), nin(nano inch), ft, stat.mile
                               : Possible scale factor: any real value more then 0. Factor to meter.
XSetPrs                        : Doc [label1 lavbel2 ...]     : Set presentation for given label(s) or whole doc
XSetTransparency               : Doc Transparency [label1 label2 ...]    : Set transparency for given label(s) or whole doc
XSetViewNameMode               : (1/0)     : Set/Unset mode of displaying names.
XShow                          : Doc [label1 lavbel2 ...]     : Display document (or some labels) in a graphical window
XShowFaceBoundary              : Doc Label IsOn [R G B [LineWidth [LineStyle]]]:- turns on/off drawing of face boundaries and defines boundary line style
XStat                          : Doc     : Print statistics of document
XTestDoc                       : XTestDoc shape
XWdump                         : Doc filename.{gif|xwd|bmp}     : Dump contents of viewer window to XWD, GIF or BMP file
Xdump                          : Doc [int deep (0/1)]     : Print information about tree's structure
XAddLayer                      : DocName StringLayer     : Adding layer in XCAFDocument.
XFindLayer                     : DocName string     : Print label where are layer is situated.
XGetAllLayers                  : DocName     : Get all layers in XCAFDocument.
XGetLayerLabels                : DocName     : Print labels from layertable.
XGetLayerRefs                  : DocName Label     : Prints layers labels which are referenced in passed label or prints labels which reference passed layer label.
XGetLayers                     : DocName {Shape|Label}     : Get layers of indicated shape
XGetOneLayer                   : DocName LayerLabel     : Print name of layer.
XIsVisible                     : DocName {layerLable|StringLayer}     : Return 1 if layer is visible, 0 if not
XRemoveAllLayers               : DocName     : remove all layers from XCAFDocument.
XRemoveLayer                   : DocName {Label|string}     :remove layer from XCAFDocument.
XSetLayer                      : DocName {Shape|Label} StringLayer [shapeInOneLayer(0/1)]     : Set reference between Shape and Layer (add layer if nesessary). shapeInOneLayer 0 is default
XSetLinkLayer                  : DocName {Shape|Label} LayerL [shapeInOneLayer(0/1)]     : Set reference between shape and existing layer. shapeInOneLayer 0 is default
XSetVisibility                 : DocName {layerLable|StringLayer} [isvisible(1/0)]     : Set visibility of layer
XUnSetAllLayers                : DocName {Shape|Label}     : unset shape from all layers.
XUnSetLayer                    : DocName {Shape|Label} stringL     : unset shape from indicated layer.
XCheckProps                    : DocName [ 0|deflection [Shape|Label] ]    : Check properties recorded for shape 
XGetArea                       : DocName {Shape|Label}     : Getting area of shape
XGetCentroid                   : DocName {Shape|Label}     : Getting centroid of shape 
XGetValProps                   : Doc {Label|Shape}
XGetVolume                     : DocName {Shape|Label}     : Getting volume of shape
XSetArea                       : DocName {Label|Shape} area     : Setting area to shape
XSetCentroid                   : DocName  {Label|Shape} x y z     : Setting centroid to shape
XSetMaterial                   : Doc {Label|Shape} name density(g/cu sm)     : Set material to shape given by Label
XSetProps                      : DocName {Shape|Label} [epsilon = 0.001]     : Compute properties for shape 
XSetVolume                     : DocName {Label|Shape} volume     : Setting volume to shape
XShapeMassProps                : XShapeMassProps DocName [deflection [Shape|Label] ]    : Get mass value and center of gravity for shape 
XShapeVolume                   : Shape     : Calculating volume of shape
XAddComponent                  : Doc Label Shape     : Add component shape to assembly
XAddShape                      : Doc Shape [makeAssembly = 1]    : Add shape (or assembly) to Document
XAddSubShape                   : Doc Shape ParentLabel     : Add subshape under given parent shape label
XAutoNaming                    : Doc [0|1]    : Disable/enable autonaming to Document
XDumpLocation                  : Doc Label     : Dump Transformation() of XCAFDoc_Location attribute
XFindComponent                 : Doc Shape     : prints sequence of labels of assembly path
XFindMainShape                 : Doc SubShape     : Find main shape for given subshape
XFindSHUO                      : Doc labels of SHUO structure     : prints label of SHUO that found by labels structure
XFindShape                     : Doc Shape [findInstance (0/1), 0 by default]    : Find and print label with indicated top-level shape
XFindSubShape                  : Doc Shape ParentLabel     : Find subshape under given parent shape label
XGetAllSHUO                    : Doc Comp_Label     : remove SHUO of indicated component
XGetAllSHUOInstances           : Doc res SHUO_Label     : returns SHUO_styled shapes as compound
XGetFreeShapes                 : Doc [shape_prefix]    : Print labels or create DRAW shapes for all free shapes in the Doc
XGetNU_SHUO                    : Doc UU_Label     : prints the NextUsages of indicated UpperUsage
XGetOneShape                   : shape Doc     : Put all free shapes of the Doc into single DRAW shape
XGetProperties                 : Doc Label     : prints named properties assigned to the Label
XGetReferredShape              : Doc Label     : Print label, that contain a top-level shape, that corresponds shape at following label
XGetSHUOInstance               : Doc res SHUO_Label     : returns SHUO_styled shape
XGetShape                      : Result Doc Label     : Put shape from tree to Result
XGetTopLevelShapes             : Doc     : Print labels, that contain a top-level shapes
XGetUU_SHUO                    : Doc NU_Label     : prints the UpperUsages of indicated NextUsage
XGetUsers                      : Doc Label [withSubChilds(int)]     : Print number of assemblies that use shape at following label
XIsHasSHUO                     : Doc SHUO_Label     : remove SHUO of indicated component
XLabelInfo                     : Doc Label     : Print information about object at following label
XNbComponents                  : Doc Label [withSubChilds(int)]     : Print number of component of assembly 
XNewShape                      : Doc     : Create new empty top-level shape
XRemoveComponent               : Doc Label     : Remove component from components label
XRemoveSHUO                    : Doc SHUO_Label     : remove SHUO of indicated component
XRemoveShape                   : Doc Label     : Remove shape from document
XSetInstanceSHUO               : Doc shape     : sets the SHUO structure for indicated component
XSetSHUO                       : Doc UU_Label [ multi-level labels ] NU_Label     : sets the SHUO structure between UpperUsage and NextUsage
XSetShape                      : Doc Label Shape     : Set shape at indicated label
XUpdateAssemblies              : Doc     : updates assembly compounds
ReadIges                       : Doc filename: Read IGES file to DECAF document
ReadStep                       : Doc filename [mode]
                               : Read STEP file to a document.
WriteIges                      : Doc filename: Write DECAF document to IGES file
WriteStep                      : Doc filename [mode=a [multifile_prefix] [label]]: Write DECAF document to STEP file
WriteVrml                      : Doc filename [version VRML#1.0/VRML#2.0 (1/2): 2 by default] [representation shaded/wireframe/both (0/1/2): 0 by default]
XExpand                        : XExpand Doc recursively(0/1) or XExpand Doc recursively(0/1) label1 label2 ...or XExpand Doc recursively(0/1) shape1 shape2 ...
XExtract                       : XExtract dstDoc [dstAssmblSh] srcDoc srcLabel1 srcLabel2 ...    Extracts given srcLabel1 srcLabel2 ... from srcDoc into given Doc or assembly shape
XFileCur                       : : returns name of file which is set as current
XFileList                      : Print list of files that was transferred by the last transfer
XFileSet                       : filename: Set the specified file to be the current one
XFromShape                     : shape: do fromshape command for all the files
?                              : Liste les commandes. ? <titre> : commandes debutant par <titre>
d                              : d [view-id], rotate down
l                              : l [view-id], rotate left
r                              : r [view-id], rotate right
u                              : u [view-id], rotate up
stepschemaxcommand             : controle de commande. command tout court pour help complet
xhelp                          : Liste les commandes. ? <titre> : commandes debutant par <titre>
xnew                           : creation item : donner nom_item puis commande args
xsource                        : lit les commandes depuis un fichier
xstep                          : prefixe neutre pour xstep-draw
listdrawings                   : Liste Drawings. Nom selection sinon tout modele
listsviews                     : Liste Vues SIMPLES. Nom selection sinon tout modele
listviews                      : Liste Vues (tous types). Nom selection sinon tout modele
setuseflag                     : useflag givelist  :  Set Use Flag to value
ReadGltf                       : ReadGltf Doc file [-parallel {on|off}] [-listExternalFiles] [-noCreateDoc] [-doublePrecision {on|off}]
                               : Read glTF file into XDE document.
                               :   -listExternalFiles do not read mesh and only list external files
                               :   -noCreateDoc read into existing XDE document
                               :   -doublePrecision store triangulation with double or single floating point
                               :                    precision (single by default)
                               :   -skipLateLoading data loading is skipped and can be performed later
                               :                    (false by default)
                               :   -keepLate data is loaded into itself with preservation of information
                               :             about deferred storage to load/unload this data later.
ReadObj                        : ReadObj Doc file [-fileCoordSys {Zup|Yup}] [-fileUnit Unit]
                               :                  [-resultCoordSys {Zup|Yup}] [-singlePrecision]
                               :                  [-listExternalFiles] [-noCreateDoc]
                               : Read OBJ file into XDE document.
                               :   -fileUnit       length unit of OBJ file content;
                               :   -fileCoordSys   coordinate system defined by OBJ file; Yup when not specified.
                               :   -resultCoordSys result coordinate system; Zup when not specified.
                               :   -singlePrecision truncate vertex data to single precision during read; FALSE by default.
                               :   -listExternalFiles do not read mesh and only list external files.
                               :   -noCreateDoc    read into existing XDE document.
WriteGltf                      : WriteGltf Doc file [-trsfFormat {compact|TRS|mat4}]=compact
                               :                    [-systemCoordSys {Zup|Yup}]=Zup
                               :                    [-comments Text] [-author Name]
                               :                    [-forceUVExport]=0 [-texturesSeparate]=0 [-mergeFaces]=0 [-splitIndices16]=0
                               :                    [-nodeNameFormat {empty|product|instance|instOrProd|prodOrInst|prodAndInst|verbose}]=instOrProd
                               :                    [-meshNameFormat {empty|product|instance|instOrProd|prodOrInst|prodAndInst|verbose}]=product
                               : Write XDE document into glTF file.
                               :   -trsfFormat preferred transformation format
                               :   -systemCoordSys system coordinate system; Zup when not specified
                               :   -mergeFaces     merge Faces within the same Mesh
                               :   -splitIndices16 split Faces to keep 16-bit indices when -mergeFaces is enabled
                               :   -forceUVExport  always export UV coordinates
                               :   -texturesSeparate write textures to separate files
                               :   -nodeNameFormat name format for Nodes
                               :   -meshNameFormat name format for Meshes
WriteObj                       : WriteObj Doc file [-fileCoordSys {Zup|Yup}] [-fileUnit Unit]
                               :                   [-systemCoordSys {Zup|Yup}]
                               :                   [-comments Text] [-author Name]
                               : Write XDE document into OBJ file.
                               :   -fileUnit       length unit of OBJ file content;
                               :   -fileCoordSys   coordinate system defined by OBJ file; Yup when not specified.
                               :   -systemCoordSys system coordinate system; Zup when not specified.
loadvrml                       : shape file
mesh3delem                     : creates 3d element mesh to test
mesh_edge_width                : set width of edges
meshclosed                     : meshclosed meshname (0/1) 
                               : Change MeshVS_Mesh drawing mode. 0 - not closed object, 1 - closed object
meshcolors                     : display color presentation
meshdeform                     : display deformed mesh
meshfromstl                    : creates MeshVS_Mesh from STL file
meshhide                       : erase MeshVS_Mesh object
meshhidesel                    : hide selected entities
meshinfo                       : displays the number of nodes and triangles
meshlinkcolor                  : change MeshVS_Mesh line color
meshmat                        : change MeshVS_Mesh material and transparency
meshshadcolor                  : change MeshVS_Mesh shading color
meshshow                       : display MeshVS_Mesh object
meshshowall                    : show all entities
meshshowsel                    : show only selected entities
meshshrcoef                    : change MeshVS_Mesh shrink coeff
meshtext                       : display text labels
meshvectors                    : display sample vectors
readgltf                       : readgltf shape file
                               : Same as ReadGltf but reads glTF file into a shape instead of a document.
readobj                        : readobj shape file [-fileCoordSys {Zup|Yup}] [-fileUnit Unit]
                               :                    [-resultCoordSys {Zup|Yup}] [-singlePrecision]
                               :                    [-singleFace]
                               : Same as ReadObj but reads OBJ file into a shape instead of a document.
                               :   -singleFace merge OBJ content into a single triangulation Face.
readstl                        : readstl shape file [-brep] [-mergeAngle Angle]
                               : Reads STL file and creates a new shape with specified name.
                               : When -brep is specified, creates a Compound of per-triangle Faces.
                               : Single triangulation-only Face is created otherwise (default).
                               : -mergeAngle specifies maximum angle in degrees between triangles to merge equal nodes; disabled by default.
writegltf                      : writegltf shape file
writeobj                       : writeobj shape file
writestl                       : shape file [ascii/binary (0/1) : 1 by default] [InParallel (0/1) : 0 by default]
writevrml                      : shape file [version VRML#1.0/VRML#2.0 (1/2): 2 by default] [representation shaded/wireframe/both (0/1/2): 1 by default]
LocDump                        : a: dump location of a
LocSet                         : a [b [c]]: set loc b->a; use no args to get help
changecurvcolor                : changecurvcolor color curve: change color of the curve
                               : 
                               : The possible colors are: 
                               :   white, red, green, blue, cyan,
                               :   golden, magenta, brown, orange, pink,
                               :   salmon, violet, yellow, darkgreen, coral
changepointcolor               : changepointcolor color point: change color of the point
                               : 
                               : The possible colors are: 
                               :   white, red, green, blue, cyan,
                               :   golden, magenta, brown, orange, pink,
                               :   salmon, violet, yellow, darkgreen, coral
changepointmarker              : changepointmarker marker point: change marker of the point
                               : 
                               : The possible markers are: 
                               :   square, diamond, x, plus, circle, circle_zoom
clknots                        : clknots [name], no args : modal 
clpoles                        : clpoles [name], no args : modal 
defle                          : defle [names...] defle
discr                          : discr [names...] nbintervals
dmode                          : dmode [names...] Uniform/Discret
nbiso                          : nbiso name [names...] nuiso nviso
setcurvcolor                   : setcurvcolor [color] : set curve color by default, or print the current curve color if no argument (this does not modify the color of the curve)
                               : 
                               : The possible colors are: 
                               :   white, red, green, blue, cyan,
                               :   golden, magenta, brown, orange, pink,
                               :   salmon, violet, yellow, darkgreen, coral
setpointcolor                  : setpointcolor [color] : set point color by default, or print the current point color if no argument (this does not modify the color of the point)
                               : 
                               : The possible colors are: 
                               :   white, red, green, blue, cyan,
                               :   golden, magenta, brown, orange, pink,
                               :   salmon, violet, yellow, darkgreen, coral
setpointmarker                 : setpointmarker [marker] : set point marker by default, or print the current point marker if no argument (this does not modify the marker of the point)
                               : 
                               : The possible markers are: 
                               :   square, diamond, x, plus, circle, circle_zoom
shknots                        : shknots [name], no args : modal 
shpoles                        : shpoles [name], no args : modal 

