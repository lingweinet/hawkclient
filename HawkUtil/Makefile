#添加规则
include ./Rules.mk

#子目录定义
RAPIDXML_DIR = source/rapidxml
ZLIB_DIR	 = source/zlib
JSON_DIR     = source/json
SQLITE_DIR   = source/sqlite

#引用头文件路径
INC_DIRS  += -I$(RAPIDXML_DIR) -I$(ZLIB_DIR) -I$(JSON_DIR) -I$(SQLITE_DIR)

#生成库文件
LIB_HAWKUTIL = $(BIN_DIR)/libhawkutil.a

#编译子目录
SUB_DIRS  = $(ZLIB_DIR) $(JSON_DIR) $(SQLITE_DIR)

#宏定义修改
MACROS += -DUTIL_EXPORT

#编译标签
all: $(SUB_DIRS) $(OBJ_FILES) $(LIB_HAWKUTIL)

$(SUB_DIRS): force
	$(MAKE) -C $@

$(LIB_HAWKUTIL): force
	$(AR) $@ $(OBJ_DIR)/*.o $(ZLIB_DIR)/$(OBJ_DIR)/*.o $(JSON_DIR)/$(OBJ_DIR)/*.o $(SQLITE_DIR)/$(OBJ_DIR)/*.o

clean: force
	$(RM) $(OUT_DIR)
	-($(foreach dir,$(SUB_DIRS),$(MAKE) -C $(dir) clean;))

force:
